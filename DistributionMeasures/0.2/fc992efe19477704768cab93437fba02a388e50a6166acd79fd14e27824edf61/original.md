```
struct DistributionMeasure <: AbstractMeasure
```

Wraps a `Distributions.Distribution` as a `MeasureBase.AbstractMeasure`.

Avoid calling `DistributionMeasure(d::Distribution)` directly. Instead, use `AbstractMeasure(d::Distribution)` to allow for specialized `Distribution` to `AbstractMeasure` conversions.

Use `convert(Distribution, m::DistributionMeasure)` or `Distribution(m::DistributionMeasure)` to convert back to a `Distribution`.
