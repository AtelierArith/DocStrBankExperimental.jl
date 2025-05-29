```
recursive_map(f, x, args...)
```

Similar to `fmap(f, args...)` but with restricted support for the notion of "leaf" types. However, this allows for more efficient and type stable implementations of recursive operations.

!!! warning "Deprecation Warning"
    Starting Lux v1.3.0, this function is deprecated in favor of `Functors.fmap`. Functors v0.5 made significant strides towards improving the performance of `fmap` and hence this function has been deprecated. Users are encouraged to use `Functors.fmap` instead.


## How this works?

For the following types it directly defines recursion rules:

1. `AbstractArray`: If eltype is `isbitstype`, then `f` is applied to the array, else we recurse on the array.
2. `Tuple/NamedTuple`: We recurse on the values.
3. `Number/Val/Nothing`: We directly apply `f`.
4. For all other types, we recurse on the fields using `Functors.fmap`.

!!! note
    In most cases, users should gravitate towards `Functors.fmap` if it is being used outside of hot loops. Even for other cases, it is always recommended to verify the correctness of this implementation for specific usecases.

