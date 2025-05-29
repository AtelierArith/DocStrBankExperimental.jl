```
abstract type DiscreteStyle <: SamplingStyle end
```

サンプリング演算子はグリッドでの評価に対応しています。このグリッドは、ここにリストされたスタイルによって指定されます：

[`InterpolationStyle`](@ref), [`OversamplingStyle`](@ref), [`GridStyle`](@ref)
