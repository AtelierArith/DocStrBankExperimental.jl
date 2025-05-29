```
rand_dm(dimensions; rank::Int=prod(dimensions))
```

与えられた引数 `dimensions` と `rank` を使用して、Ginibre アンサンブルからランダムな密度行列を生成し、それが正準半定であり、トレースが `1` になることを保証します。

`dimensions` は以下のいずれかの型であることができます：

  * `dimensions::Int`: ヒルベルト空間の基底状態の数。
  * `dimensions::Union{Dimensions,AbstractVector{Int},Tuple}`: 各サブシステムの基底の数を表す次元のリスト。

デフォルトのキーワード引数 `rank = prod(dimensions)`（フルランク）。

!!! warning "型の安定性に注意してください！"
    型の安定性を保ちたい場合は、`dimensions` を `Tuple` または [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) の `SVector` として `rand_dm(dimensions; rank=rank)` を使用することをお勧めします。`Vector` の代わりに。型の安定性に関する詳細については、[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) と [関連セクション](@ref doc:Type-Stability) を参照してください。


# 参考文献

  * [J. Ginibre, Statistical ensembles of complex, quaternion, and real matrices, Journal of Mathematical Physics 6.3 (1965): 440-449](https://doi.org/10.1063/1.1704292)
  * [K. Życzkowski, et al., Generating random density matrices, Journal of Mathematical Physics 52, 062201 (2011)](http://dx.doi.org/10.1063/1.3595693)
