```
split_by_season_across_time(var::OutputVar)
```

Split `var` into `OutputVar`s representing seasons, sorted in chronological order. Each `OutputVar` corresponds to a single season, and the ordering of the `OutputVar`s is determined by the dates of the season. The return type is a vector of `OutputVar`s.

The months of the seasons are March to May (MAM), June to August (JJA), September to November (SON), and December to February (DJF). If there are no dates found for a season, then the `OutputVar` for that season will be an empty `OutputVar`. The first `OutputVar` is guaranteed to not be empty. For non-empty OutputVars, the season can be found by `var.attributes["season"]`.

The function will use the start date in `var.attributes["start_date"]`. The unit of time is expected to be second.

This function differs from `split_by_season` as `split_by_season` splits dates by season and ignores that seasons can come from different years.
