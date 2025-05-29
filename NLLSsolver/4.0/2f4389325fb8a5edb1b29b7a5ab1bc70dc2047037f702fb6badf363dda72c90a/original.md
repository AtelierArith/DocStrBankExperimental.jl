```
NLLSsolver.ndeps(mycost::AbstractCost)
```

Return the number of variables that `mycost` depends on. The return value must be a static integer.

# Example

For a cost function `MyCost <: AbstractCost` that is a function of two variables, the user  should define the following function:

```julia
    NLLSsolver.ndeps(::MyCost) = static(2)
```

!!! note
    Required user-specialized API function.

