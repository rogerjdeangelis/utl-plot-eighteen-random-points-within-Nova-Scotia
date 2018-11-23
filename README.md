# utl-plot-eighteen-random-points-within-Nova-Scotia
Plot eighteen random points within Nova Scotia
    Plot eighteen random points within Nova Scotia

    Output graph
    https://tinyurl.com/ycfw348h

    github
    https://tinyurl.com/ycnahdrl
    https://github.com/rogerjdeangelis/utl-plot-eighteen-random-points-within-Nova-Scotia

    https://tinyurl.com/y996hwtl
    https://stackoverflow.com/questions/53451515/plotting-points-near-a-coastline-with-geom-point-ggmap-plot

    Hrbrmstr Profile
    https://stackoverflow.com/users/1457051/hrbrmstr


    INPUT
    =====

    Some random points inside Nova Scotia (see link) or create your own. (Long/Lat)

     SD1.HAVE total obs=18

        X        Y

      -63.4    44.7
      -63.9    45.1
      -64.2    44.7
      -60.8    46.8
      -65.0    44.3
      -63.8    45.4
      -62.7    45.3
      -66.1    44.3
      -64.8    44.1
      -64.5    44.8
      -63.8    44.5
      -64.7    44.8
      -63.1    44.9
      -65.5    43.9
      -64.6    44.4
      -60.4    45.9
      -63.9    44.6
      -62.4    45.6


    PROCESS
    =======

    %utl_submit_r64('
    library(sf);
    library(lwgeom);
    library(tidyverse);
    library(haven);
    some_random_points<-read_sas("d:/sd1/have.sas7bdat");
    canada <- st_as_sf(raster::getData("GADM", country = "CAN", level = 1));
    ns <- filter(canada, NAME_1 == "Nova Scotia");
    ns <- st_simplify(ns, preserveTopology = TRUE, 0.01);
    png(file="d:/png/utl-plot-eighteen-random-points-within-Nova-Scotias.png");
    ggplot() +
      geom_sf(data = ns, fill = "gray90", color = "#2b2b2b", size=0.125) +
      geom_point(data = some_random_points, aes(X, Y)) +
      theme_bw();
    png();
    ');

    * Ignore the warning;

    OUTPUT
    ======

    https://tinyurl.com/ycfw348h
    https://github.com/rogerjdeangelis/utl-plot-eighteen-random-points-within-Nova-Scotia/blob/master/utl-plot-eighteen-random-points-within-Nova-Scotias.png

    *                _              _       _
     _ __ ___   __ _| | _____    __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|

    ;

    options validvarname=upcase;
    libname sd1 "d:/sd1";

    data sd1.have;
     input  X  Y;
    cards4;
     -63.4  44.7
     -63.9  45.1
     -64.2  44.7
     -60.8  46.8
     -65.0  44.3
     -63.8  45.4
     -62.7  45.3
     -66.1  44.3
     -64.8  44.1
     -64.5  44.8
     -63.8  44.5
     -64.7  44.8
     -63.1  44.9
     -65.5  43.9
     -64.6  44.4
     -60.4  45.9
     -63.9  44.6
     -62.4  45.6
    ;;;;
    run;quit;



