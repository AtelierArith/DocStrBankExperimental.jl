```
NLLSsolver.varindices(mycost)
```

Return a static vector representing the indices of the variables that `mycost` depends on.

# Example

For a cost of type `MyCost <: AbstractCost` that depends on the first and third variables, the user should define the following function:

```julia
    NLLSsolver.varindices(::MyCost) = SVector(1, 3)
```

!!! note
    Required user-specialized API function.

