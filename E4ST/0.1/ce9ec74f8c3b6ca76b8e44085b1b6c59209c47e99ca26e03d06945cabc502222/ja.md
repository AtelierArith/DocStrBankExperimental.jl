```
aggregate_generation(data, grouping_col, idxs=(:), yr_idxs=(:), hr_idxs=(:)) -> d::OrderedDict
```

`grouping_col`で発電結果を集約します。キーがグループ化キーで、値が生成されたエネルギーであるOrderedDictを返します。`idxs`、`yr_idxs`、および`hr_idxs`は柔軟に設定できます（[`get_row_idxs`](@ref)、[`get_year_idxs`](@ref)、および[`get_hour_idxs`](@ref）を参照）。
