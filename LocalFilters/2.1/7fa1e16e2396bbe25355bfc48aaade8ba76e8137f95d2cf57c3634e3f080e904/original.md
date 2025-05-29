```
localmean([T,] A, B=3; null=zero(T), order=FORWARD_FILTER)
```

yields the local mean of `A` in a neighborhood defined by `B`. The result is an array similar to `A`. If `B` is not specified, the neighborhood is a hyper-rectangular sliding window of size 3 in every dimension. Otherwise, `B` may be specified as a Cartesian box, or as an array of booleans of same number of dimensions as `A`. If `B` is a single odd integer (as it is by default), the neighborhood is assumed to be a hyper-rectangular sliding window of size `B` in every dimension.

Optional argument `T` is to specify the element type of the result.

Keyword `null` may be used to specify the value of the result where the sum of the weights in a local neighborhood is zero. By default, `null = zero(T)`.

Keyword `order` specifies the filter direction, `FORWARD_FILTER` by default.

See also [`localmean!`](@ref) and [`localfilter!`](@ref).
