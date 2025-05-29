```
ConstantSamplesRoundingMode(start::RoundingMode)
```

Creates a rounding object for [`AlignedSpan`](@ref) to indicate the `AlignedSpan` should be constructed by the `start` and `duration` of the `span`, without regard to its `stop`.

If two `span`s have the same duration, then the resulting `AlignedSpan`'s will have the same number of samples when constructed with this rounding mode.

See also [`AlignedSpan(sample_rate, span, mode::ConstantSamplesRoundingMode)`](@ref).
