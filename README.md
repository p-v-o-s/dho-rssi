
<img src='./images/signalStrength.png' height=200> <img src='./images/terrain.png' height=200>


# Overview

This project involved logging sensor data to a file on a computer (in this case, remotely, via radio transmission) while simultaneously recording GPS location using a smartphone app.  Because GPS recording devices (like smartphones) are common, and generate KML or GPX files, the resultant problem may fairly common: how to combine the GPS data (logging at some rate) with the sensor data (logging at some other rate).

Because we imagine that each part of this process might separately have useful application in various monitoring use-cases, we have broken our analysis into three main steps:

## Converting a gpx file to csv

The original gpx file, in XML format, can be converted to a simplified csv format that's easier to work with, using the format:

```
 unix epoch, latitude, longitude, elevation, speed 
```

We've done that in the notebook named [gpx_to_csv.ipynb](./gpx_to_csv.ipynb) .

## Combining gps data with logging data

The gps data (now in csv format, via the above transformation) can then be matched with the logging file by comparing timestamp information and finding the 'closest match'. 

We've done that in a notebook here: [timing_match.ipynb](./timing_match.ipynb) .

## Plotting the combined file on a map

Finally, the world-line of the logging data (in our case, the signal strength (RSSI) of a radio transmitter) can be embedded in a map.  

We've used the Folium library to do that here:  [folium_plot.ipynb](./folium_plot.ipynb) .

