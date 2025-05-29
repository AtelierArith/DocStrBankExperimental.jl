```
format(f::PiecewiseFunction)
```

Return a string holding the constructor for the `PiecewiseFunction` object `f`. For [`Formula`](@ref) objects than have a name, the name is used instead of the constructor of the `Formula` object. Note that `print(f)` is equivalent to `print(format(f))`.
