# 概要

ARTモデルを、オプションの監視ラベルを持つ特徴'x'の単一サンプルでトレーニングします。

# 引数

  * `art::ART`: トレーニングする非監視ARTモデル。
  * `x::RealVector`: トレーニングに使用する単一サンプルの特徴ベクトル。
  * `y::Integer=0`: オプション、単純な監視トレーニングのためのラベル。
  * `preprocessed::Bool=false`: オプション、データがすでに補完符号化されているかどうかのフラグ。

# メソッドリスト / 定義場所

```julia
train!(art, x; y, preprocessed)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl:275`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl)で定義されています。

```julia
train!(art, x; y, preprocessed)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl:268`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl)で定義されています。

```julia
train!(art, x; y, preprocessed)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl:300`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl)で定義されています。
