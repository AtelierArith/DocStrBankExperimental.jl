# 概要

監視ラベル 'y' を持つ特徴 'x' の単一サンプルで監視型ARTMAPモデルをトレーニングします。

# 引数

  * `art::ARTMAP`: トレーニングする監視型ARTモデル。
  * `x::RealVector`: トレーニングに使用する単一サンプル特徴ベクトル。
  * `y::Integer`: 監視トレーニングのためのラベル。
  * `preprocessed::Bool=false`: データがすでに補完符号化されているかどうかのオプションフラグ。

# メソッドリスト / 定義場所

```julia
train!(art, x, y; preprocessed)
```

[`packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl:235`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl) で定義されています。
