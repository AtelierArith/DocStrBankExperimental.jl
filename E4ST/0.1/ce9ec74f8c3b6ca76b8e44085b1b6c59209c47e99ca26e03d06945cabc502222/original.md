```
aggregate_generation(data, grouping_col, idxs=(:), yr_idxs=(:), hr_idxs=(:)) -> d::OrderedDict
```

Aggregate the generation results by `grouping_col`.  Returns an OrderedDict where the keys are the grouping key, and the values are the energy generated.  `idxs`, `yr_idxs` and `hr_idxs` can be flexible (see [`get_row_idxs`](@ref), [`get_year_idxs`](@ref), and [`get_hour_idxs`](@ref)).
