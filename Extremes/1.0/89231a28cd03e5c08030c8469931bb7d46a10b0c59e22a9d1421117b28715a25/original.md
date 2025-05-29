```
returnlevel(fm::pwmAbstractExtremeValueModel{ThresholdExceedance, T} where T<:Distribution, threshold::Real, nobservation::Int,
    nobsperblock::Int, returnPeriod::Real)::ReturnLevel
```

Compute the return level corresponding to the return period `returnPeriod` from the fitted model `fm`.

The threshold should be a scalar. A varying threshold is not yet implemented.
