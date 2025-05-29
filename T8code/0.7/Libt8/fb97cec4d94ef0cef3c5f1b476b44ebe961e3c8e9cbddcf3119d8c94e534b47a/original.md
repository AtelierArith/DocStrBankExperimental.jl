```
t8_vec_eq(vec_x, vec_y, tol)
```

Check the equality of two vectors elementwise

# Arguments

  * `vec_x`:[in]
  * `vec_y`:[in]
  * `tol`:[in]

# Returns

true, if the vectors are equal up to *tol*

### Prototype

```c
static inline int t8_vec_eq (const double vec_x[3], const double vec_y[3], const double tol);
```
