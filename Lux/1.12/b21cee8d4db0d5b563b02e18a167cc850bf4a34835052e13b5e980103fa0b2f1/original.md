```
recursive_add!!(x, y)
```

Recursively add the leaves of two nested structures `x` and `y`. In Functor language, this is equivalent to doing `fmap(+, x, y)`, but this implementation uses type stable code for common cases.

Any leaves of `x` that are arrays and allow in-place addition will be modified in place.

!!! warning "Deprecation Warning"
    Starting Lux v1.3.0, this function is deprecated in favor of `Functors.fmap`. Functors v0.5 made significant strides towards improving the performance of `fmap` and hence this function has been deprecated. Users are encouraged to use `Functors.fmap` instead.

