```
complexity(c::ComplexityEstimator, x) → m::Real
```

Estimate a complexity measure according to `c` for [input data](@ref input_data) `x`, where `c` is an instance of any subtype of [`ComplexityEstimator`](@ref):

  * [`ApproximateEntropy`](@ref).
  * [`LempelZiv76`](@ref).
  * [`MissingDispersionPatterns`](@ref).
  * [`ReverseDispersion`](@ref).
  * [`SampleEntropy`](@ref).
  * [`BubbleEntropy`](@ref).
  * [`StatisticalComplexity`](@ref).
