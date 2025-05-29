```
recursive_make_zero!!(x)
```

Recursively create a zero value for a nested structure `x`. Leaves that can be mutated with in-place zeroing will be modified in place.

See also [`Lux.recursive_make_zero`](@ref) for fully out-of-place version.

!!! warning "Deprecation Warning"
    Starting Lux v1.3.0, this function is deprecated in favor of `Functors.fmap`. Functors v0.5 made significant strides towards improving the performance of `fmap` and hence this function has been deprecated. Users are encouraged to use `Functors.fmap` instead.

