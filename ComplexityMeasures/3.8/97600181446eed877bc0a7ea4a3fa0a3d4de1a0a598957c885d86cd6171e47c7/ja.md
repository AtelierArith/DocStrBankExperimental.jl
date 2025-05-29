```
complexity(c::ComplexityEstimator, x) → m::Real
```

`c`に従って[入力データ](@ref input_data) `x`の複雑さの尺度を推定します。ここで、`c`は[`ComplexityEstimator`](@ref)の任意のサブタイプのインスタンスです：

  * [`ApproximateEntropy`](@ref).
  * [`LempelZiv76`](@ref).
  * [`MissingDispersionPatterns`](@ref).
  * [`ReverseDispersion`](@ref).
  * [`SampleEntropy`](@ref).
  * [`BubbleEntropy`](@ref).
  * [`StatisticalComplexity`](@ref).
