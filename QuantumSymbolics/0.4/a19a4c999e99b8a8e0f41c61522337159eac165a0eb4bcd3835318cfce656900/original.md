Completely depolarized state

```jldoctest
julia> MixedState(X1⊗X2)
𝕄

julia> express(MixedState(X1⊗X2))
Operator(dim=4x4)
  basis: [Spin(1/2) ⊗ Spin(1/2)]
 0.25 + 0.0im        ⋅             ⋅             ⋅     
       ⋅       0.25 + 0.0im        ⋅             ⋅
       ⋅             ⋅       0.25 + 0.0im        ⋅
       ⋅             ⋅             ⋅       0.25 + 0.0im

julia> express(MixedState(X1⊗X2), CliffordRepr())
𝒟ℯ𝓈𝓉𝒶𝒷
 
𝒳ₗ━━
+ X_
+ _X
𝒮𝓉𝒶𝒷
 
𝒵ₗ━━
+ Z_
+ _Z
```
