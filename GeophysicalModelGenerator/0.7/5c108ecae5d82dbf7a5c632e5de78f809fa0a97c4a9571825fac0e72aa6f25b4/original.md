```
velocity_spherical_to_cartesian!(Data::GeoData, Velocity::Tuple)
```

In-place conversion of velocities in spherical velocities `[Veast, Vnorth, Vup]` to cartesian coordinates (for use in paraview).

NOTE: the magnitude of the vector will be the same, but the individual `[Veast, Vnorth, Vup]` components will not be retained correctly (as a different `[x,y,z]` coordinate system is used in paraview). Therefore, if you want to display or color that correctly in Paraview, you need to store these magnitudes as separate fields
