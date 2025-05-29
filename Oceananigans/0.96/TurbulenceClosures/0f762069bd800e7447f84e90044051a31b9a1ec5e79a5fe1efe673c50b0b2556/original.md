```
struct VerticallyImplicitTimeDiscretization <: AbstractTimeDiscretization
```

A vertically-implicit time-discretization of a `TurbulenceClosure`.

This implies that a flux divergence such as $𝛁 ⋅ 𝐪$ at the $n$-th timestep is time-discretized as

```julia
[∇ ⋅ q]ⁿ = [explicit_flux_divergence]ⁿ + [∂z (κ ∂z c)]ⁿ⁺¹
```
