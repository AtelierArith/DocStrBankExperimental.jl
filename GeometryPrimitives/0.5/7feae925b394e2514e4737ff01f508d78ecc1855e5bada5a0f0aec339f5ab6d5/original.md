```
volfrac(voxel, nout, r₀)
```

Returns the volume fraction `rvol = vol(voxel ⋂ half-space) / vol(voxel)` that indicates how much portion of the volume of a voxel is included the half-space defined by a plane.  The result is between 0.0 and 1.0, inclusive.  Inside and outside of the half space is determined by `nout`, which is the outward normal.  (If a point is on the `nout` side of the plane, then it is outside.)

The voxel needs to be aligned with the Cartesian axes, and is described by `v = ([xn,yn,zn], [xp,yp,zp])` that specifies the x-, y-, z-boundaries of the voxel.  The half-space is described by the boundary plane.  The boundary plane is described by the outward normal vector `nout = [nx, ny, nz]` and a point `r₀ = [rx, ry, rz]` on the plane. `nout` does not have to be normalized.
