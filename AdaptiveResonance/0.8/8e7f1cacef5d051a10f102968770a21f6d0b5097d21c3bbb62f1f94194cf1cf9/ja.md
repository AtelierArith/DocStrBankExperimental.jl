```julia
complement_code(
    data::AbstractArray{T} where T<:Real;
    config
) -> Any

```

# 概要

データ x を [0, 1] に正規化し、拡張ベクトル [x, 1 - x] を返します。

# 引数

  * `data::RealArray`: 補完符号化される 1-D または 2-D データ。
  * `config::DataConfig=DataConfig()`: ART/ARTMAP モジュールのデータ構成。

# メソッドリスト / 定義場所

```julia
complement_code(data; config)
```

[`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:402`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl) で定義されています。
