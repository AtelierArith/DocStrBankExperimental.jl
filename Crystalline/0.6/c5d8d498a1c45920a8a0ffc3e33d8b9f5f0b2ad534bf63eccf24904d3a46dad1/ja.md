```
realify(pgirs::AbstractVector{T}) where T<:AbstractIrrep --> Vector{T}
```

従来の不変表現（例えば、[`pgirreps`](@ref)によって生成される）から物理的に実数の不変表現（コア不変表現）を返します。点群のような`AbstractIrrep`のフォールバックメソッドです。

## 例

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
