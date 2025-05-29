```
fussy_measure(measure; extra_check=nothing)
```

Return a new measure, `fussy`, with the same behavior as `measure`, except that calling `fussy` on data, or calling `measuremnts` on `fussy` and data, will will additionally:

  * Check that if `weights` or `class_weights` are specified, then `measure` supports them (see [`StatisticalMeasuresBase.check_weight_support`](@ref))
  * Check that `ŷ` (predicted proxy), `y` (ground truth), `weights` and `class_weights` are compatible, from the point of view of observation counts and class pools, if relevant (see and [`StatisticalMeasuresBase.check_numobs`](@ref) and [`StatisticalMeasuresBase.check_pools`](@ref)).
  * Call `extra_check(measure, ŷ, y[, weights, class_weights])`, unless `extra_check==nothing`. Note the first argument here is `measure`, not `atomic_measure`.

Do not use `fussy_measure` unless both `y` and `ŷ` are expected to implement the MLUtils.jl `getobs`/`numobs` interface (e.g., are `AbstractArray`s)

See also [`StatisticalMeasuresBase.measurements`](@ref), [`StatisticalMeasuresBase.is_measure`](@ref)
