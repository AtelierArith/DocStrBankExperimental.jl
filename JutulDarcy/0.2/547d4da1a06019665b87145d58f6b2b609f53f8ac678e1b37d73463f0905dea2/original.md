```
ReservoirSimResult(model, result::Jutul.SimResult, forces, extra = Dict(); kwarg...)
```

Create a specific reservoir simulation results that contains well curves, reservoir states, and so on. This is the return type from `simulate_reservoir`.

A `ReservoirSimResult` can be unpacked into well solutions, reservoir states and reporting times:

```julia
res_result::ReservoirSimResult
ws, states, t = res_result
```

# Fields

  * `wells`
  * `states`
  * `time`
  * `result`
  * `extra`
