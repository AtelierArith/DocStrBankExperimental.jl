# 概要

ARTモデルを使用して、特徴の単一サンプル'x'のカテゴリを予測します。

予測されたカテゴリ'y_hat'を返します。

# 引数

  * `art::ARTModule`: バッチ推論に使用するARTまたはARTMAPモジュール。
  * `x::RealVector`: 分類するための特徴の単一サンプル。
  * `preprocessed::Bool=false`: データがすでに補完符号化されているかどうかのオプションフラグ。
  * `get_bmu::Bool=false`: モデルが完全な不一致の場合に最適一致ユニットラベルを返すべきかどうかのオプションフラグ。

# メソッドリスト / 定義場所

```julia
classify(art, x; preprocessed, get_bmu)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl:362`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl)で定義されています。

```julia
classify(art, x; preprocessed, get_bmu)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl:360`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl)で定義されています。

```julia
classify(art, x; preprocessed, get_bmu)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl:392`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl)で定義されています。

```julia
classify(art, x; preprocessed, get_bmu)
```

[`packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl:315`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl)で定義されています。
