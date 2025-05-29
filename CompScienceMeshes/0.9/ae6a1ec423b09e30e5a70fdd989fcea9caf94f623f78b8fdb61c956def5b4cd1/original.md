```
gmshcuboid(width, height, length, delta)
```

Creates a mesh for a cuboid of width (along the x-axis) `width`, height (along     the y-axis) `height` and length (along the z-axis) `length` by parsing a .geo script     incorporating these parameters into the GMSH mesher.

The target edge size is `delta`. physical => in {"TopPlate", "BottomPlate", "SidePlates", "OpenBox"} extracts and returns only the specified part of the cuboid
