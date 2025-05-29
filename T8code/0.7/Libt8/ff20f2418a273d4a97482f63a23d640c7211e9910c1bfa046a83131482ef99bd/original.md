```
t8_mat_mult_mat(A, B, C)
```

Apply matrix-matrix multiplication: C = A*B.

# Arguments

  * `A`:[in] 3x3-matrix.
  * `B`:[in] 3x3-matrix.
  * `C`:[in] 3x3-matrix.

### Prototype

```c
static inline void t8_mat_mult_mat (const double A[3][3], const double B[3][3], double C[3][3]);
```
