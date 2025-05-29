```julia
struct LogProgressReport{T}
```

Report progress into the `Logging` framework, using `@info`.

For the information reported, a *step* is a NUTS transition, not a leapfrog step.

# Fields

  * `chain_id`: ID of chain. Can be an arbitrary object, eg `nothing`.
  * `step_interval`: Always report progress past `step_interval` of the last report.
  * `time_interval_s`: Always report progress past this much time (in seconds) after the last report.
