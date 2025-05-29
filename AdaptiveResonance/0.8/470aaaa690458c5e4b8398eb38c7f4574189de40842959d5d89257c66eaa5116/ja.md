```julia
data_setup!(
    config::AdaptiveResonance.DataConfig,
    data::AbstractMatrix{T} where T<:Real
)

```

# 概要

トレーニングの前にARTモジュールのデータ設定を行います。

この関数は、データの元の次元と補完符号化された次元を取得し、各特徴次元に沿った最大値と最小値からデータの範囲（最小値と最大値）を推測します。

# 引数

  * `config::DataConfig`: ART/ARTMAPモジュールのデータ設定オブジェクト。
  * `data::RealMatrix`: データ設定を作成するために使用する2次元のデータバッチ。

# メソッドリスト / 定義場所

```julia
data_setup!(config, data)
```

[`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:268`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl)で定義されています。
