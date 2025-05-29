```
Scheduler{TSolution <: Solution}
```

Type for metaheuristics that work by iteratively applying certain methods/operations.

# Elements

  * `incumbent`: incumbent solution, i.e., initial solution and always best solution so far   encountered
  * `incumbent_valid`: `true` if incumbent is a valid solution to be considered
  * `incumbent_iteration`: iteration in which incumbent was found
  * `incumbent_time`: time at which incumbent was found
  * `methods`: vector of all `MHMethods`
  * `method_stats`: dict of `MHMethodStatistics` for each `MHMethod`
  * `iteration`: overall number of method applications
  * `time_start`: starting time of algorithm
  * `run_time`: overall runtime (set when terminating)
  * `params`: parameters adopted from settings by default
