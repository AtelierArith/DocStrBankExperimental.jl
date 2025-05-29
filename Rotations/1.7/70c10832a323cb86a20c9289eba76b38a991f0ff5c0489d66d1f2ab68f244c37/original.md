```
isrotation(r)
isrotation(r, tol)
```

Check whether `r` is a rotation matrix, where `r * r'` is within `tol` of the identity matrix (using the Frobenius norm). `tol` defaults to `1000 * eps(float(eltype(r)))` or `zero(T)` for integer `T`.
