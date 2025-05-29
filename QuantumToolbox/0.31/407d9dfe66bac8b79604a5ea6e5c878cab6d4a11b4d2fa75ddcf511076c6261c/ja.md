```
zero_ket(dimensions)
```

与えられた引数 `dimensions` を持つゼロ [`Ket`](@ref) ベクトルを返します。

`dimensions` は次のいずれかの型であることができます：

  * `dimensions::Int`: ヒルベルト空間の基底状態の数。
  * `dimensions::Union{Dimensions,AbstractVector{Int}, Tuple}`: 各サブシステムの基底の数を表す次元のリスト。

!!! warning "型の安定性に注意してください！"
    型の安定性を保つために、`dimensions` を `Tuple` または [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) の `SVector` として `zero_ket(dimensions)` を使用することを強く推奨します。型の安定性に関する詳細は、[関連セクション](@ref doc:Type-Stability) を参照してください。

