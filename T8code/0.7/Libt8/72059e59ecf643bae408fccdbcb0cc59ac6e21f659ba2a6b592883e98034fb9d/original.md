```
t8_vec_diff(vec_x, vec_y, diff)
```

Compute the difference of two vectors.

# Arguments

  * `vec_x`:[in] A 3D vector.
  * `vec_y`:[in] A 3D vector.
  * `diff`:[out] On output, the difference of *vec_x* and *vec_y*.

### Prototype

```c
static inline void t8_vec_diff (const double vec_x[3], const double vec_y[3], double diff[3]);
```
