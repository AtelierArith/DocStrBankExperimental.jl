```
maximally_mixed_dm(dimensions)
```

与えられた引数 `dimensions` に対して、最大混合密度行列を返します。

`dimensions` は次のいずれかの型であることができます：

  * `dimensions::Int`: ヒルベルト空間の基底状態の数。
  * `dimensions::Union{Dimensions,AbstractVector{Int},Tuple}`: 各サブシステムの基底の数を表す次元のリスト。

!!! warning "型の安定性に注意してください！"
    型の安定性を保ちたい場合は、`maximally_mixed_dm(dimensions)` を `Tuple` または [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) の `SVector` として `dimensions` を使用することをお勧めします。型の安定性に関する詳細は、[関連セクション](@ref doc:Type-Stability)を参照してください。

