```
set_flow!(job::Job, should_runs::Pair{String, Bool}...)
```

Sets whether or not calculations should be scheduled to run. The `name` of each calculation in the job will be checked against the string in each pair of `should_runs`, and the `calculation.run` will be set accordingly.

Example:

```julia
set_flow!(job, "" => false, "scf" => true)
```

would un-schedule all calculations in the job, and schedule the "scf" and "nscf" calculations to run.
