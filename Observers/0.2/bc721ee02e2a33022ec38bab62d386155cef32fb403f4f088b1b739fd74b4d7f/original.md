```
update!(
  df::AbstractDataFrame,
  args...;
  update!_kwargs=(; promote=true, skip_all_missing=true, skip_all_nothing=true),
  kwargs...,
)
```

Update the data frame `df` by executing the functions stored on each column, passing the arguments `args...` and keyword arguments `kwargs...` to each function.

By default, `update!` promotes the type of the column data if needed, if new data can't be converted to the current data type of the column. That can be disabled by setting `push!_kwargs=(; promote=false)`.

Also, by default, rows that have all `missing` data or all `nothing` data don't get pushed into the `df`. That can be disabled by setting `update!_kwargs=(; skip_all_missing=false)` and/or `update!_kwargs=(; skip_all_nothing=false)`.
