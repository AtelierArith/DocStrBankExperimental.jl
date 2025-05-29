```
make_ito_process_syncronous_time_series(ito_processes::Union{Dict{Symbol,ItoProcess{T}},Dict{Symbol,ItoProcess}},
                                                 covar::Union{ForwardCovariance,SimpleCovariance}, timegap::R, total_number_of_ticks::Integer;
                                                 number_generator::NumberGenerator = Mersenne(MersenneTwister(2), length(collect(keys(ito_processes))))) where R<:Real where T<:Real
```

Evolve the `ItoProcess`es forward.

### Inputs

  * `itoprocesses` - A `Dict` of `ItoProcess`es
  * `covar` - The covariance matrix.
  * `timegap` - The time gap between ticks.
  * `total_number_of_ticks` - The total number of ticks.
  * `number_generator` The `NumberGenerator` used for the RNG.

### Return

  * A DataFrame with the ticks.
