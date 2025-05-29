```
setwswindow(xmin::Real, xmax::Real, ymin::Real, ymax::Real)
```

Set the area of the NDC viewport that is to be drawn in the workstation window.

**Parameters:**

`xmin` :     The left horizontal coordinate of the workstation window. `xmax` :     The right horizontal coordinate of the workstation window (0 <= `xmin` < `xmax` <= 1). `ymin` :     The bottom vertical coordinate of the workstation window. `ymax` :     The top vertical coordinate of the workstation window (0 <= `ymin` < `ymax` <= 1).

`setwswindow` defines the rectangular area of the Normalized Device Coordinate space to be output to the device. By default, the workstation transformation will map the range [0,1] x [0,1] in NDC onto the largest square on the workstation’s display surface. The aspect ratio of the workstation window is maintained at 1 to 1.
