```
setwindow(xmin::Real, xmax::Real, ymin::Real, ymax::Real)
```

`setwindow` establishes a window, or rectangular subspace, of world coordinates to be plotted. If you desire log scaling or mirror-imaging of axes, use the SETSCALE function.

**Parameters:**

`xmin` :     The left horizontal coordinate of the window (`xmin` < `xmax`). `xmax` :     The right horizontal coordinate of the window. `ymin` :     The bottom vertical coordinate of the window (`ymin` < `ymax`). `ymax` :     The top vertical coordinate of the window.

`setwindow` defines the rectangular portion of the World Coordinate space (WC) to be associated with the specified normalization transformation. The WC window and the Normalized Device Coordinates (NDC) viewport define the normalization transformation through which all output primitives are mapped. The WC window is mapped onto the rectangular NDC viewport which is, in turn, mapped onto the display surface of the open and active workstation, in device coordinates. By default, GR uses the range [0,1] x [0,1], in world coordinates, as the normalization transformation window.
