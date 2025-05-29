```
t8_vec_axb(vec_x, vec_y, alpha, b)
```

Y = alpha * X + b

!!! note
    It is possible that vec_x = vec_y on input to overwrite x


# Arguments

  * `vec_x`:[in] A 3D vector.
  * `vec_y`:[out] On input, a 3D vector. On output set to *alpha* * *vec_x* + *b*.
  * `alpha`:[in] A factor.
  * `b`:[in] An offset.

### Prototype

```c
static inline void t8_vec_axb (const double vec_x[3], double vec_y[3], const double alpha, const double b);
```
