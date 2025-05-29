```
run_threaded_scenarios(s::Scenarios, optimizer; remove_series=false)
```

Run batches of REopt scenarios in parallel according to `Scenarios.Nparallel` and return a vector of dictionaries for results.

If `remove_series` is `true` then all time series results are removed from the dictionaries, which will keep memory use lower and make the results compatible with rectangular data stores.
