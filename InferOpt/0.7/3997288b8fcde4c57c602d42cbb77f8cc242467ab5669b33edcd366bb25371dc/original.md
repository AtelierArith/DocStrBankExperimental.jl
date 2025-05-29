```julia
struct LinearMaximizer{F, G, H}
```

Wrapper for generic minear maximizers of the form argmax_y θᵀg(y) + h(y). It is compatible with the following layers

  * [`PerturbedAdditive`](@ref) (with or without a [`FenchelYoungLoss`](@ref))
  * [`PerturbedMultiplicative`](@ref) (with or without a [`FenchelYoungLoss`](@ref))
  * [`SPOPlusLoss`](@ref)

# Fields

  * `maximizer::Any`: function θ ⟼ argmax_y θᵀg(y) + h(y)
  * `g::Any`: function g(y) used in the objective
  * `h::Any`: function h(y) used in the objective
