```
chebinterp_v1(vals, lb, ub; tol=eps)
```

Like `chebinterp(vals, lb, ub)`, but slices off the *first* dimension of `vals` and treats it as a vector of values to interpolate.

For example, if `vals` is a 2×31×32 array of numbers, then it is treated equivalently to calling `chebinterp` with a 31×32 array of 2-component vectors.

(This function is mainly useful for calling from Python, where arrays of vectors are painful to construct.)
