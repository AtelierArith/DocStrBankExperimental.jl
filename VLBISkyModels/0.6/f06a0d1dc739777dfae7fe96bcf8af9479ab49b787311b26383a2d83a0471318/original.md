```julia
struct Shift{T, T1, T2} <: VLBISkyModels.ModelModifier{T}
```

Shifts the model by `Δx` units in the x-direction and `Δy` units in the y-direction.

# Example

```julia-repl
julia> modify(Gaussian(), Shift(2.0, 1.0)) == shifted(Gaussian(), 2.0, 1.0)
true
```
