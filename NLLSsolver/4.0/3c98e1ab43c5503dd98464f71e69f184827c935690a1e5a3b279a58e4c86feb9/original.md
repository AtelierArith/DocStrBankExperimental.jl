```
NLLSsolver.nres(mycost)
```

Return the number of residuals that `mycost` generates. The return value must be an integer, preferably static, and must not change during an optimization.

# Example

For a residual block type `MyResidual <: AbstractResidual` that returns a residual vector of length three from its `computeresidual` method,

```julia
    NLLSsolver.nres(::MyCost) = static(3)
```

!!! tip
    If the residual length is known at compile time, return a static integer.


!!! note
    Required user-specialized API function.

