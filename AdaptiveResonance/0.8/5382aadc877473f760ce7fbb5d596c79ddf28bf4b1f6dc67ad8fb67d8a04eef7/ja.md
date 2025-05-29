```julia
DataConfig(
    mins::AbstractVector{T} where T<:Real,
    maxs::AbstractVector{T} where T<:Real
) -> AdaptiveResonance.DataConfig

```

# 概要

DataConfigの便利なコンストラクタで、特徴の最小値と最大値のみを必要とします。

このコンストラクタは、最小値と最大値が特徴ごとに異なる場合に使用されます。次元は最小値と最大値の長さから推測されます。

# 引数

  * `mins::RealVector`: 各特徴次元の最小値のベクトル。
  * `maxs::RealVector`: 各特徴次元の最大値のベクトル。

# メソッドリスト / 定義場所

```julia
DataConfig(mins, maxs)
```

[`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:79`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl)で定義されています。
