クリフォード演算子は基底生成子のマッピングによって指定されます。

```jldoctest
julia> tCNOT
X₁ ⟼ + XX
X₂ ⟼ + _X
Z₁ ⟼ + Z_
Z₂ ⟼ + ZZ

julia> phase_gate = C"Y
                      Z"
X₁ ⟼ + Y
Z₁ ⟼ + Z

julia> stab = S"XI
                IZ";


julia> entangled = tCNOT*stab
+ XX
+ ZZ

julia> CliffordOperator(T"YY")
ERROR: DimensionMismatch: Input tableau should be of size 2n×n (top half is the X mappings and the bottom half are the Z mappings).
[...]
```

[`Destabilizer`](@ref) も変換可能です。

```jldoctest
julia> d = Destabilizer(S"Y")
𝒟ℯ𝓈𝓉𝒶𝒷
+ Z
𝒮𝓉𝒶𝒷
+ Y

julia> CliffordOperator(d)
X₁ ⟼ + Z
Z₁ ⟼ + Y
```
