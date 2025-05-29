```
taylor_expand(f, x0; order)
```

Computes the Taylor expansion of the function `f` around the point `x0`.

If `x0` is a scalar, a `Taylor1` expansion will be returned. If `x0` is a vector, a `TaylorN` expansion will be computed. If the dimension of x0 (`length(x0)`) is different from the variables set for `TaylorN` (`get_numvars()`), an `AssertionError` will be thrown.
