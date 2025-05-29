```
split_by_season(var::OutputVar)
```

Return a vector of four `OutputVar`s split by season.

The months of the seasons are March to May (MAM), June to August (JJA), September to November (SON), and December to February (JDF). The order of the vector is MAM, JJA, SON, and DJF. If there are no dates found for a season, then the `OutputVar` for that season will be an empty `OutputVar`. For non-empty OutputVars, the season can be found by `var.attributes["season"]`.

The function will use the start date in `var.attributes["start_date"]`. The unit of time is expected to be second.

!!! note "Interpolating between seasons"
    Interpolations will be inaccurate in time intervals outside of their respective season for the returned `OutputVar`s. For example, if an `OutputVar` has the dates 2010-2-1, 2010-3-1, 2010-4-1, and 2011-2-1 after splitting by seasons, then any interpolation in time between the dates 2010-4-1 and 2011-2-1 will be inaccurate.


This function differs from `split_by_season_across_time` as `split_by_season_across_time` splits dates by season for each year.
