```
unfussy(measure)
```

Return a version of `measure` with argument checks removed, if that is possible. Specifically, if `measure == fussy_measure(atomic_measure)`, for some `atomic_measure`, then return `atomic_measure`. Otherwise, return `measure`.

See also [`StatisticalMeasuresBase.fussy_measure`](@ref).
