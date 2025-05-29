```
scale_boundary(boundary, scale_factor)
```

Scale the sides of a bounding box by a scaling factor.

The scaling factor can be a single number or a `SVector` of the appropriate number of dimensions corresponding to the scaling factor for each axis. For a 3D bounding box the volume scales as the cube of the scaling factor.
