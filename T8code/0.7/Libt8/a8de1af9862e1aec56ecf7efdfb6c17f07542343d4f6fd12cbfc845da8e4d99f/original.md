```
t8_vec_ax(vec_x, alpha)
```

Compute X = alpha * X

# Arguments

  * `vec_x`:[in,out] A 3D vector. On output set to *alpha* * *vec_x*.
  * `alpha`:[in] A factor.

### Prototype

```c
static inline void t8_vec_ax (double vec_x[3], const double alpha);
```
