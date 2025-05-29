```
t8_mat_init_zrot(mat, angle)
```

Initialize given 3x3 matrix as rotation matrix around the z-axis with given angle.

# Arguments

  * `mat`:[in,out] 3x3-matrix.
  * `angle`:[in] Rotation angle in radians.

### Prototype

```c
static inline void t8_mat_init_zrot (double mat[3][3], const double angle);
```
