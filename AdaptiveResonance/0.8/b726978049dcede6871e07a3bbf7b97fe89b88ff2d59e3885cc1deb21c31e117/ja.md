```julia
DataConfig(
    min::Real,
    max::Real,
    dim::Integer
) -> AdaptiveResonance.DataConfig

```

# 概要

DataConfigの便利なコンストラクタで、グローバルなmin、max、およびdimのみを必要とします。

このコンストラクタは、特徴の最小値と最大値がすべてそれぞれ同じである場合に使用されます。

# 引数

  * `min::Real`: すべての特徴にわたる最小値。
  * `max::Real`: すべての特徴にわたる最大値。
  * `dim::Integer`: 特徴の次元で、最小値または最大値だけからは推測できないため、提供する必要があります。

# メソッドリスト / 定義場所

```julia
DataConfig(min, max, dim)
```

[`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:104`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl)で定義されています。
