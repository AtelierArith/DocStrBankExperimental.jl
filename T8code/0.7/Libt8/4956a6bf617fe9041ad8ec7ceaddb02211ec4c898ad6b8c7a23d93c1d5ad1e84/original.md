```
t8_mat_mult_vec(mat, a, b)
```

Apply matrix-matrix multiplication: b = M*a.

# Arguments

  * `mat`:[in] 3x3-matrix.
  * `a`:[in] 3-vector.
  * `b`:[in,out] 3-vector.

### Prototype

```c
static inline void t8_mat_mult_vec (const double mat[3][3], const double a[3], double b[3]);
```
