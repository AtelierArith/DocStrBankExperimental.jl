```
@ForwardDiff_frule signature mutating
```

`mutating` indicates whether or not the function is mutating the input argument.

# Example

To define a rule for `LinearAlgebra.exp!`, which is a mutating funciton, we call the macro like this

```julia
@ForwardDiff_frule LinearAlgebra.exp!(A::AbstractMatrix{<:ForwardDiff.Dual}) true
```
