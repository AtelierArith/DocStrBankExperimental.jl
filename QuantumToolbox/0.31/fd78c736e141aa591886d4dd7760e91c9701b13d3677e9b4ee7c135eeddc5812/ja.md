```
rand_unitary(dimensions, distribution=Val(:haar))
```

ランダムなユニタリ [`QuantumObject`](@ref) を返します。

`dimensions` は以下のいずれかの型であることができます：

  * `dimensions::Int`: ヒルベルト空間の基底状態の数。
  * `dimensions::Union{Dimensions,AbstractVector{Int},Tuple}`: 各サブシステムの基底の数を表す次元のリスト。

`distribution` はユニタリ行列を取得するために使用される方法を指定します：

  * `:haar`: 参照1のアルゴリズムを使用したHaarランダムユニタリ行列
  * `:exp`: $\exp(-i\hat{H})$ を使用します。ここで、$\hat{H}$ はランダムに生成されたエルミート演算子です。

# 参考文献

1. [F. Mezzadri, How to generate random matrices from the classical compact groups, arXiv:math-ph/0609050 (2007)](https://arxiv.org/abs/math-ph/0609050)

!!! warning "型の安定性に注意してください！"
    型の安定性を保ちたい場合は、`rand_unitary(dimensions, Val(distribution))` を使用することをお勧めします。`rand_unitary(dimensions, distribution)` の代わりに。また、`dimensions` を [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) の `Tuple` または `SVector` として指定してください。型の安定性に関する詳細は、[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) および [関連セクション](@ref doc:Type-Stability) を参照してください。

