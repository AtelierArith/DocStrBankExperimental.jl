```
g = Geometry([;kwargs...])
```

Returns a geometry object associated with the CloudSeis data-set.  This includes an origin (`o`) and three orthogonal vectors (`u`,`v`,`w`).  In addition, one can specify how azimuth is defined for TTI earth models by giving a specific direction for positive azimuth, and the axis from which it is measured.  This can be useful when describing the orientation of a model in three dimensional space.

# key-word arguments

  * `ox=0,oy=0,oz=0` grid origin
  * `ux=0,uy=0,uz=1` u vector such that the end of the u axis is at the point (ox+ux,oy+uy,oz+uz)
  * `vx=0,vy=0,vz=1` v vector such that the end of the u axis is at the point (ox+vx,oy+vy,oz+vz)
  * `wx=0,wy=0,wz=1` w vector such that the end of the u axis is at the point (ox+wx,oy+wy,oz+wz)
  * `u1=1,un=2` integer end-points (u axis) that can be used to describe a grid (e.g. for finite difference)
  * `v1=1,vn=2` integer end-points (v axis) that can be used to describe a grid (e.g. for finite difference)
  * `w1=1,wn=2` integer end-points (w axis) that can be used to describe a grid (e.g. for finite difference)
  * `umin=0.0,umax=1.0` portion of geometry (u axis) that is used for the model
  * `vmin=0.0,vmax=1.0` portion of geometry (v axis) that is used for the model
  * `wmin=0.0,wmax=1.0` portion of geometry (w axis) that is used for the model
  * `x_direction="east"` compass direction that 'x' is parallel to
  * `y_direction="north"` compass direction that 'y' is parallel to
  * `z_direction="depth"` compass direction that 'z' is parallel to
  * `tti_angle_units="degrees"` for TTI models specify if the tilt and azimuth angles are stored in ("degrees", "radians", or "unknown")
  * `tti_azimuth_positive_direction="counter clockwise"` for TTI models, define the orientation of the azimuth ("clockwise", "counter clockwise" or "unknown")
  * `tti_azimuth_origin_axis="v"` for TTI models, define the axis from which azimuth is measured and at which azimuth is 0 (choose from: "u", "v", "w", "x", "y", "-u", "-v", "-w", "-x", "-y" or "unknown")
  * `tti_symmetry_axis_z_direction="elevation"` for TTI models, define if the projection of the normal to the symmetry axis onto z = (0,0,1) point up (elevation) or down (depth)

# notes

  * this method does not check to see if the u,v,w vectors are orthogonal
  * for models that do not required azimuthal anisotropy (e.g. isotropic, VTI), it is convenient to set `tti_azimumth_positive_direction` and `tti_azimuth_origin_axis` to "unknown"
  * `umin,umax,vmin,vmax,wmin,wmax` are used when a sub- or super-set of u,v,w descibe the model domain.  For example, if the magnitude of `(ux,uy,uz)` is the length of a single

model grid cell, then `umin=0` and `umax=(nu-1)` would be appropriate.
