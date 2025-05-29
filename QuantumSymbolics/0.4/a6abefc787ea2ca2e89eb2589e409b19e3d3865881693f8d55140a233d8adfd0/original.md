Projector for a given ket.

```jldoctest
julia> projector(X1⊗X2)
𝐏[|X₁⟩|X₂⟩]

julia> express(projector(X2))
Operator(dim=2x2)
  basis: Spin(1/2)
  0.5+0.0im  -0.5-0.0im
 -0.5+0.0im   0.5+0.0im
```
