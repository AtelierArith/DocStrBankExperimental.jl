viewlabspace:  Visualisation of L*a*b* space

```
Usage:    viewlabspace(L = 50, figNo = 1)

Arguments:     L - Lightness level in which to display slice of L*a*b* space
           figNo - PyPlot figure to use
```

Function allows interactive viewing of a sequence of images corresponding to different slices of lightness in L*a*b* space.  Lightness varies from 0 to

100. Initially a slice at a lightness of 50 is displayed.

Pressing 'l' or arrow up/right will increase the lightness by dL. Pressing 'd' or arrow down/left will darken by dL. Press 'x' to exit.

To Do: The CIELAB colour coordinates of the cursor position within the slice images should be updated continuously.  This is useful for determining suitable control points for the definition of colourmap paths through CIELAB space in cmap().

See also: colourmappath, cmap
