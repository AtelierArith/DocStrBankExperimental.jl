```
measurements(measure, ŷ, y[, weights, class_weights::AbstractDict])
```

Return a vector of measurements, one for each observation in `y`, rather than a single aggregated measurement. Otherwise the behavior is the same as calling the measure directly on data.

# New implementations

Overloading this function for new measure types is optional. A fallback returns the aggregated measure, repeated `n` times, where `n = MLUtils.numobs(y)` (which falls back to `length(y)` if `numobs` is not implemented).  It is not typically necessary to overload `measurements` for wrapped measures.  All [`multimeasure`](@ref)s provide the obvious fallback and other wrappers simply forward the `measurements` method of the atomic measure. If overloading, use the following signatures:

```
StatisticalMeasuresBase.measurements(measure::SomeMeasureType, ŷ, y)
StatisticalMeasuresBase.measurements(measure::SomeMeasureType, ŷ, weights)
StatisticalMeasuresBase.measurements(measure::SomeMeasureType, ŷ, class_weights::AbstractDict)
StatisticalMeasuresBase.measurements(measure::SomeMeasureType, ŷ, weights, class_weights)
```
