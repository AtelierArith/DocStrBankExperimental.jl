```
realify(pgirs::AbstractVector{T}) where T<:AbstractIrrep --> Vector{T}
```

Return physically real irreps (coreps) from a set of conventional irreps (as produced by e.g. [`pgirreps`](@ref)). Fallback method for point-group-like `AbstractIrrep`s.

## Example

```jl-doctest
julia> pgirs = pgirreps("4", Val(3));
julia> characters(pgirs)
CharacterTable{3}: ⋕9 (4)
───────┬────────────────────
       │ Γ₁  Γ₂    Γ₃    Γ₄ 
───────┼────────────────────
     1 │  1   1     1     1
  2₀₀₁ │  1   1    -1    -1
 4₀₀₁⁺ │  1  -1   1im  -1im
 4₀₀₁⁻ │  1  -1  -1im   1im
───────┴────────────────────

julia> characters(realify(pgirs))
CharacterTable{3}: ⋕9 (4)
───────┬──────────────
       │ Γ₁  Γ₂  Γ₃Γ₄ 
───────┼──────────────
     1 │  1   1     2
  2₀₀₁ │  1   1    -2
 4₀₀₁⁺ │  1  -1     0
 4₀₀₁⁻ │  1  -1     0
───────┴──────────────
```
