```
times = get_adc_sampling_times(seq)
```

Returns an array of times when the samples of the sequence `seq` are acquired.

# Arguments

  * `seq`: (`::Sequence`) sequence struct

# Returns

  * `times`: (`::Vector{Float64}`, `[s]`) time array when samples are acquired
