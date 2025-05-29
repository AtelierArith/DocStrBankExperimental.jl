```
t8_vec_axy(vec_x, vec_y, alpha)
```

Compute Y = alpha * X

# Arguments

  * `vec_x`:[in] A 3D vector.
  * `vec_z`:[out] On output set to *alpha* * *vec_x*.
  * `alpha`:[in] A factor.

### Prototype

```c
static inline void t8_vec_axy (const double vec_x[3], double vec_y[3], const double alpha);
```
