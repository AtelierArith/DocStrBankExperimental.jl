すべてのメトリックリーダーは `close(::AbstractMetricReader)` と `(r::AbstractMetricReader)()` を実装する必要があります。

ビルトインリーダー:

  * [`CompositMetricReader`](@ref)
  * [`MetricReader`](@ref)
  * [`PeriodicMetricReader`](@ref)
