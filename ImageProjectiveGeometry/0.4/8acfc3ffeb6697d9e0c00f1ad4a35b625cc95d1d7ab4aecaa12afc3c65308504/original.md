plotcamera - Plots graphical representation of camera(s) showing pose.

```
Usage: plotcamera(C, l; col=[0,0,1], plotCamPath=false, fig=nothing)

Arguments:
           C - Camera structure (or array of Camera structures)
           l - The length of the sides of the rectangular cone indicating
               the camera's field of view.
Keyword Arguments:
         col - Optional three element vector specifying the RGB colour to
               use. Defaults to blue.
 plotCamPath - Optional flag true/false to plot line joining camera centre
               positions. If omitted or empty defaults to false.
         fig - Optional figure number to be used. If not specified a new
               figure is created.
```

The function plots into the current figure a graphical representation of one or more cameras showing their pose.  This consists of a rectangular cone, with its vertex at the camera centre, indicating the camera's field of view. The camera's coordinate X and Y axes are also plotted at the camera centre.

See also: Camera
