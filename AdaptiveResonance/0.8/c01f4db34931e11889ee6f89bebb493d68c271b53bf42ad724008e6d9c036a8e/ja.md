```julia
linear_normalization(
    data::AbstractVector{T} where T<:Real;
    config
) -> Vector{Float64}

```

# 概要

データを各特徴に沿って範囲 [0, 1] に正規化します。

# 引数

  * `data::RealVector`: 正規化する1次元データサンプル。
  * `config::DataConfig=DataConfig()`: ART/ARTMAPモジュールからのデータ設定。

# メソッドリスト / 定義場所

```julia
linear_normalization(data; config)
```

[`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:339`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl) で定義されています。
