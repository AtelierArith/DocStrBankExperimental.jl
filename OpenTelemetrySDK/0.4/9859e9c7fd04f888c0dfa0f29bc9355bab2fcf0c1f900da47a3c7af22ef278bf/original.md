All metric readers should implement `close(::AbstractMetricReader)` and `(r::AbstractMetricReader)()`.

Builtin readers:

  * [`CompositMetricReader`](@ref)
  * [`MetricReader`](@ref)
  * [`PeriodicMetricReader`](@ref)
