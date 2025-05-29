```
State( ρ :: Matrix{T<:Number} ) <: Operator{T}
```

量子状態の密度行列表現。コンストラクタ `State(ρ)` は、[`is_density_matrix`](@ref) が `false` を返す場合に `DomainError` をスローします。
