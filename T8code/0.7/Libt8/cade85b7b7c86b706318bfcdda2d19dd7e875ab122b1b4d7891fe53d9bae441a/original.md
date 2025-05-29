```
t8_vec_axpy(vec_x, vec_y, alpha)
```

Y = Y + alpha * X

# Arguments

  * `vec_x`:[in] A 3D vector.
  * `vec_y`:[in,out] On input, a 3D vector. On output set *to* vec_y + *alpha* * *vec_x*
  * `alpha`:[in] A factor.

### Prototype

```c
static inline void t8_vec_axpy (const double vec_x[3], double vec_y[3], const double alpha);
```
