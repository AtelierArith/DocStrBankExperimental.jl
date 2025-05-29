```
t8_vec_axpyz(vec_x, vec_y, vec_z, alpha)
```

Z = Y + alpha * X

# Arguments

  * `vec_x`:[in] A 3D vector.
  * `vec_y`:[in] A 3D vector.
  * `vec_z`:[out] On output set *to* vec_y + *alpha* * *vec_x*

### Prototype

```c
static inline void t8_vec_axpyz (const double vec_x[3], const double vec_y[3], double vec_z[3], const double alpha);
```
