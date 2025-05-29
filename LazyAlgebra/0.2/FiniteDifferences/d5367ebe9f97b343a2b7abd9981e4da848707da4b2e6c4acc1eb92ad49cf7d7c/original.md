```
Diff([opt::MayOptimize.Vectorize,] n=1, dims=:)
```

yields a linear mapping that computes a finite difference approximation of the `n`-order derivative along the dimension(s) specified by `dims`.  Arguments `dims` is an integer, a tuple or a vector of integers specifying along which dimension(s) to apply the operator or `:` to specify all dimensions.  If multiple dimensions are specified, the result is as if the operator is applied separately on the specified dimension(s).

Optional argument `opt` is the optimization level and may be specified as the first or last argument.  By default, `opt` is assumed to be `Vectorize`, however depending on the dimensions of the array, the dimensions of interest and on the machine, setting `opt` to `InBounds` may be more efficient.

If `dims` is a scalar, the result, say `y`, of applying the finite difference operator to an array, say `x`, has the same axes as `x`.  Otherwise and even though `x` has a single dimension or `dims` is a 1-tuple, `y` has one more dimension than `x`, the last dimension of `y` is used to store the finite differences along each dimensions specified by `dims` and the leading dimensions of `y` are the same as the dimensions of `x`.

More specifically, the operator created by `Diff` implements **forward finite differences** with **flat boundary conditions**, that is to say extrapolated entries are assumed equal to the nearest entry.
