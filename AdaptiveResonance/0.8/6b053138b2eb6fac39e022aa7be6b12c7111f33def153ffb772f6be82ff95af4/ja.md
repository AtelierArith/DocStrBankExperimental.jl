```julia
data_setup!(
    art::AdaptiveResonance.ARTModule,
    data::AbstractMatrix{T} where T<:Real
)

```

# 概要

ARTモジュールのDataConfigを事前に設定するための便利なメソッドです。

# 引数

  * `art::ARTModule`: データ設定を手動で構成するART/ARTMAPモジュール。
  * `data::RealArray`: データ設定を作成するために使用される2-Dバッチデータ。

# メソッドリスト / 定義場所

```julia
data_setup!(art, data)
```

[`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:295`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl)で定義されています。
