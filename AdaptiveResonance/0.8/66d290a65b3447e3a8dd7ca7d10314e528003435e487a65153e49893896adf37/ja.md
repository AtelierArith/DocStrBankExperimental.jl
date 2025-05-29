```julia
linear_normalization(
    data::AbstractMatrix{T} where T<:Real;
    config
) -> Any

```

# 概要

データを各特徴に沿って範囲 [0, 1] に正規化します。

# 引数

  * `data::RealMatrix`: 正規化する2次元データのバッチ。
  * `config::DataConfig=DataConfig()`: ART/ARTMAPモジュールからのデータ設定。

# メソッドリスト / 定義場所

```julia
linear_normalization(data; config)
```

[`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:369`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl) で定義されています。
