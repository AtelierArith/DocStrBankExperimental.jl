```julia
train!(
    art::AdaptiveResonance.ARTMAP,
    x::AbstractMatrix{T} where T<:Real,
    y::AbstractVector{T} where T<:Integer
) -> Any
train!(
    art::AdaptiveResonance.ARTMAP,
    x::AbstractMatrix{T} where T<:Real,
    y::AbstractVector{T} where T<:Integer,
    preprocessed::Bool
) -> Any

```

# 概要

```
train!(art::ARTMAP, x::RealMatrix, y::IntegerVector, preprocessed::Bool=false)
```

監督ラベル 'y' を持つデータ 'x' のバッチで ARTMAP モデルを訓練します。

# 引数

  * `art::ARTMAP`: 訓練する監督付き ARTMAP モデル。
  * `x::RealMatrix`: 特徴の行を持つサンプルの列を含む 2 次元データセット。
  * `y::IntegerVector`: 監督訓練のためのラベル。
  * `preprocessed::Bool=false`: データがすでに補完符号化されているかどうかのフラグ。

# メソッドリスト / 定義場所

```julia
train!(art, x, y)
train!(art, x, y, preprocessed)
```

[`packages/AdaptiveResonance/wgSPV/src/ARTMAP/common.jl:23`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/common.jl) で定義されています。
