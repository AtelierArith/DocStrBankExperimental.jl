```
get_elnom_load(data, load_idx, year_idx, hour_idxs) -> ed::Float64 (MWh)

get_elnom_load(data, load_idxs, year_idx, hour_idxs) -> ed::Float64 (MWh) (sum)

get_elnom_load(data, pair(s), year_idx, hour_idxs) -> ed::Float64 (MWh) (sum)
```

Return the energy load by load elements corresponding to `load_idx` or `load_idxs`, for `year_idx` and `hour_idx`.  Note `year_idx` can be the index or the year string (i.e. "y2030").

If pair(s) are given, filters the load elements by pair.  i.e. pairs = ("nation"=>"narnia", "read_type"=>"residential").
