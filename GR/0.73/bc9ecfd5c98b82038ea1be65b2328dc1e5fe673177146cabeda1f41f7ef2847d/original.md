```
setviewport(xmin::Real, xmax::Real, ymin::Real, ymax::Real)
```

`setviewport` establishes a rectangular subspace of normalized device coordinates.

**Parameters:**

`xmin` :     The left horizontal coordinate of the viewport. `xmax` :     The right horizontal coordinate of the viewport (0 <= `xmin` < `xmax` <= 1). `ymin` :     The bottom vertical coordinate of the viewport. `ymax` :     The top vertical coordinate of the viewport (0 <= `ymin` < `ymax` <= 1).

`setviewport` defines the rectangular portion of the Normalized Device Coordinate (NDC) space to be associated with the specified normalization transformation. The NDC viewport and World Coordinate (WC) window define the normalization transformation through which all output primitives pass. The WC window is mapped onto the rectangular NDC viewport which is, in turn, mapped onto the display surface of the open and active workstation, in device coordinates.
