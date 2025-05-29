hline - Plot a 2D line defined in homogeneous coordinates.

Function for ploting 2D homogeneous lines defined by 2 points or a line defined by a single homogeneous vector

```
Usage 1:   hline(p1,p2, linestyle="b-")
Arguments: p1, p2 -  Two 3-vectors defining points in homogeneous
                     coordinates

Usage 2:    hline(l, linestyle="b-")
Argument:   l - A 3-vector defining a line in homogeneous coordinates

```

Note that in the case where a homogeneous line is supplied as the argument the extent of the line drawn depends on the current axis limits.  This will require you to set the desired limits with a call to PyPlot.axis() prior to calling this function.
