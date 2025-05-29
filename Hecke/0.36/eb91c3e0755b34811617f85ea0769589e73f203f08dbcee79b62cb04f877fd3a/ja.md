```
abelian_group(::Type{T} = FinGenAbGroup, M::AbstractMatrix{<:IntegerUnion})
```

関係行列 `M` を持つアーベル群を作成します。つまり、群は `ncols(M)` 個の生成子を持ち、`M` の各行は1つの関係を記述します。
