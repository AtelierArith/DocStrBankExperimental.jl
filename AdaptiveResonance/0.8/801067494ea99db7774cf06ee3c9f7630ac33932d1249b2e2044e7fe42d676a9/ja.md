```julia
performance(
    y_hat::AbstractVector{T} where T<:Integer,
    y::AbstractVector{T} where T<:Integer
) -> Any

```

# 概要

y_hatとyのカテゴリパフォーマンスを取得するための便利な関数です。

# 引数

  * `y_hat::IntegerVector`: 推定されたラベル。
  * `y::IntegerVector`: 真のラベル。

# メソッドリスト / 定義場所

```julia
performance(y_hat, y)
```

[`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:200`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl)で定義されています。
