```
SharedStatsStep{Alias, F<:Function, ById}
```

A [`StatsStep`](@ref) が、[`AbstractStatsProcedure`](@ref) のサブタイプである手続きの複数のインスタンスによって共有される可能性があります。 [`PooledStatsProcedure`](@ref) と [`pool`](@ref) も参照してください。

# フィールド

  * `step::StatsStep{Alias, F, ById}`: 共有される可能性のある `step`。
  * `ids::Vector{Int}`: `step` を共有する手続きのインデックス。
