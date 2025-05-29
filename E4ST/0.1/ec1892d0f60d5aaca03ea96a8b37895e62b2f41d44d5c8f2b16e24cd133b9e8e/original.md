```
match_nominal_load!(config, data)
```

Match the yearly load by area given in `config[:load_match_file]`, updates the `pd` field of the `data[:bus]`.  See [`summarize_table(::Val{:load_match})`](@ref) for more details.

Often, we want to force the total energy load for a set of load elements over a year to match load projections from a data source.  The `load_match_table` allows the user to provide yearly energy load targets, in $MWh$, to match.  The matching weights each hourly load by the number of hours spent at each of the representative hours, as provided in the `hours` table, converting from $MW$ power load over the representative hour, into $MWh$.
