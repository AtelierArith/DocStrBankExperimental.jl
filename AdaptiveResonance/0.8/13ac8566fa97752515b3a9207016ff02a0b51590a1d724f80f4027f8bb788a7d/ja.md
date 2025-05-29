```julia
get_data_characteristics(
    data::AbstractMatrix{T} where T<:Real;
    config
) -> NTuple{4, Any}

```

# 概要

データの特性を取得します。データ構成が渡された場合はそれを考慮します。

DataConfigが渡されない場合、データの特性は配列自体から取得されます。それ以外の場合は、データの統計に構成を使用し、サンプル数にはデータ配列を使用します。

# 引数

  * `data::RealMatrix`: 補完符号化される2次元データ。
  * `config::DataConfig=DataConfig()`: ART/ARTMAPモジュールのためのデータ構成。

# メソッドリスト / 定義場所

```julia
get_data_characteristics(data; config)
```

[`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:310`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl)で定義されています。
