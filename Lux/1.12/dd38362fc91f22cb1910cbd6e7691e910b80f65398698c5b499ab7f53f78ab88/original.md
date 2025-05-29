```
recursive_make_zero(x)
```

Recursively create a zero value for a nested structure `x`. This is equivalent to doing `fmap(zero, x)`, but this implementation uses type stable code for common cases.

See also [`Lux.recursive_make_zero!!`](@ref).

!!! warning "Deprecation Warning"
    Starting Lux v1.3.0, this function is deprecated in favor of `Functors.fmap`. Functors v0.5 made significant strides towards improving the performance of `fmap` and hence this function has been deprecated. Users are encouraged to use `Functors.fmap` instead.

