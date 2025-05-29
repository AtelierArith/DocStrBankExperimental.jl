```
extremevaltheory_dims_persistences(x::AbstractStateSpaceSet, est; kwargs...)
```

Return the local dimensions `Δloc` and the persistences `θloc` for each point in the given set according to extreme value theory [Lucarini2016](@cite). The type of `est` decides which approach to use when computing the dimension. The possible estimators are:

  * [`BlockMaxima`](@ref)
  * [`Exceedances`](@ref)

The computation is parallelized to available threads (`Threads.nthreads()`).

See also [`extremevaltheory_gpdfit_pvalues`](@ref) for obtaining confidence on the results.

## Keyword arguments

  * `show_progress = true`: displays a progress bar.
  * `compute_persistence = true:` whether to aso compute local persistences `θloc` (also called extremal indices). If `false`, `θloc` are `NaN`s.
