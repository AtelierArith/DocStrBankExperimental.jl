CDCost

[`DAG`](@ref) のコストを [`GlobalMetricEstimator`](@ref) によって推定したものの表現。

# フィールド:

`.data`: 総データ転送量。 `.compute_effort`: 総計算努力。 `.compute_intensity`: 計算強度で、常に `.compute_effort / .data` に等しい。

!!! note
    `compute_intensity` は、操作コストのみの文脈では必ずしも意味を持たないことに注意してください。`graph_cost` の推定値に加算/減算する際には、意図した通りに機能します。

