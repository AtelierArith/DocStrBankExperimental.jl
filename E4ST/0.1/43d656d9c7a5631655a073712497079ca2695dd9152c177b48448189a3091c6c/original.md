```
update_build_status!(config, data, table_name)
```

Change the build_status of generators built in the simulation.

  * `unbuilt -> new` if `last(pcap)` is above threshold
  * `built -> retired_exog` if retired due to surpassing `year_shutdown`
  * `built -> retired_endog` if retired due before `year_shutdown`
