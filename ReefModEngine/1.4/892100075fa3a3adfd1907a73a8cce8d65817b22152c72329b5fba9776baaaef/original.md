```
concat_results!(rs::ResultStore, start_year::Int64, end_year::Int64, reps::Int64)::Nothing
```

Append results for all runs/replicates.

# Arguments

  * `rs` : Result store to save data to
  * `start_year` : Collect data from this year
  * `end_year` : Collect data to this year
  * `reps` : Total number of expected replicates
