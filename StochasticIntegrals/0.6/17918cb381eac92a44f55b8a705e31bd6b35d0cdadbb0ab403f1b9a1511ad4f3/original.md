```
make_ito_process_non_syncronous_time_series(ito_processes::Union{Dict{Symbol,ItoProcess{R}},Dict{Symbol,ItoProcess}},
                                                 covar::Union{ForwardCovariance,SimpleCovariance}, update_rates::Union{OrderedDict{Symbol,D},Dict{Symbol,D},OrderedDict{Symbol,Distribution},Dict{Symbol,Distribution}},
                                                 total_number_of_ticks::Integer;
                                                 timing_twister::Union{StableRNG,MersenneTwister} = MersenneTwister(1),
                                                 ito_number_generator::NumberGenerator = Mersenne(MersenneTwister(2), length(collect(keys(ito_processes))))
                                                 ) where R<:Real where D<:Distribution
```

Evolve the `ItoProcess`es forward.

### Inputs

  * `itoprocesses` - A `Dict` of `ItoProcess`es
  * `covar` - The covariance matrix.
  * `update_rates` - The update rates of the exponential waiting times between ticks for each asset.
  * `total_number_of_ticks` - The total number of ticks.
  * `ito_twister` The `MersenneTwister` used for the RNG.

### Return

  * A DataFrame with the ticks.
