```
abstract type ProjectionStyle <: SamplingStyle end
```

サンプリング演算子は射影に対応します（内積を使用）。内積の種類は[`GramStyle`](@ref)、[`DiscreteGramStyle`](@ref)、[`RectangularGramStyle`](@ref)によって指定されます。
