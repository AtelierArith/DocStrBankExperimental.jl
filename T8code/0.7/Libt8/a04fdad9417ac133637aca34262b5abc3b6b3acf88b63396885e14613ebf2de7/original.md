```
t8_mat_init_yrot(mat, angle)
```

Initialize given 3x3 matrix as rotation matrix around the y-axis with given angle.

# Arguments

  * `mat`:[in,out] 3x3-matrix.
  * `angle`:[in] Rotation angle in radians.

### Prototype

```c
static inline void t8_mat_init_yrot (double mat[3][3], const double angle);
```
