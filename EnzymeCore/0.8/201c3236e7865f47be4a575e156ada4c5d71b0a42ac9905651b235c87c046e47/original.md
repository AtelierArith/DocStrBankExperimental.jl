```
Active(x)
```

Mark a function argument `x` of [`autodiff`](@ref Enzyme.autodiff) as active, Enzyme will auto-differentiate in respect `Active` arguments.

!!! note
    Enzyme gradients with respect to integer values are zero. [`Active`](@ref) will automatically convert plain integers to floating point values, but cannot do so for integer values in tuples and structs.

