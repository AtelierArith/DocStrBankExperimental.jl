```
parse_logs_df(end_state::Dict)
```

Takes the `end_state` dictionary returned by an ABIDES simulation, goes through all the agents, extracts their log, and un-nest them returns a single dataframe with the logs from all the agents warning.
