```julia
train!(
    art::AdaptiveResonance.ART,
    x::AbstractMatrix{T} where T<:Real;
    y,
    preprocessed
) -> Any

```

# 概要

ARTモデルをバッチデータ'x'で、オプションの監視ラベル'y'を用いて訓練します。

# 引数

  * `art::ART`: 訓練する非監視ARTモデル。
  * `x::RealMatrix`: サンプルの列と特徴の行を含む2次元データセット。
  * `y::IntegerVector=Int[]`: オプション、単純な監視訓練のためのラベル。
  * `preprocessed::Bool=false`: オプション、データがすでに補完符号化されているかどうかのフラグ。

# メソッドリスト / 定義場所

```julia
train!(art, x; y, preprocessed)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/common.jl:21`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/common.jl)で定義されています。
