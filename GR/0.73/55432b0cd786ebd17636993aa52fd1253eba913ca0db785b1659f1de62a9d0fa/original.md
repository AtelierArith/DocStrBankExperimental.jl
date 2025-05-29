```
polarcellarray(xorg::Real, yorg::Real, phimin::Real, phimax::Real, rmin::Real, rmax::Real, imphi::Int, dimr::Int, color)
```

Display a two dimensional color index array mapped to a disk using polar coordinates.

**Parameters:**

`xorg` :     X coordinate of the disk center in world coordinates `yorg` :     Y coordinate of the disk center in world coordinates `phimin` :     start angle of the disk sector in degrees `phimax` :     end angle of the disk sector in degrees `rmin` :     inner radius of the punctured disk in world coordinates `rmax` :     outer radius of the punctured disk in world coordinates `dimiphi`, `dimr` :     Phi (X) and iR (Y) dimension of the color index array `color` :     Color index array

The two dimensional color index array is mapped to the resulting image by interpreting the X-axis of the array as the angle and the Y-axis as the radius. The center point of the resulting disk is located at `xorg`, `yorg` and the radius of the disk is `rmax`.
