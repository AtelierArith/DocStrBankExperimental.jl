```julia
DataConfig(
    data::AbstractMatrix{T} where T<:Real
) -> AdaptiveResonance.DataConfig

```

# 概要

データ構成を推測するためにデータ行列のみを必要とするDataConfigの便利なコンストラクタです。

# 引数

  * `data::RealMatrix`: データ構成を推測するために使用される2次元のデータバッチ。

# メソッドリスト / 定義場所

```julia
DataConfig(data)
```

[`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:120`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl)で定義されています。
