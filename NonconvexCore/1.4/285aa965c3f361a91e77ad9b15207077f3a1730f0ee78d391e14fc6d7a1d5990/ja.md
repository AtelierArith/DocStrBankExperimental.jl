```
Model(::Type{T}, f::Union{Nothing, Function}) where {T}
```

空のモデルを構築し、目的関数 `f` と決定変数の値の型 `Vector{T}` を指定します。`f` は `Base.Function` のインスタンスであることができますが、数値を返す必要があります。また、[`Objective`](@ref) のインスタンスであることもできます。`f` は `nothing` であることもでき、その場合、目的関数は後で [`set_objective!`](@ref) を使用して定義できます。
