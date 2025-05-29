```
add_baseline_and_extend_tail(wv::RadiationDetectorSignals.RDWaveform{T,U,TV,UV}, n_baseline_samples::Int, total_waveform_length::Int) where {T,U,TV,UV}
```

Adds a zero-valued baseline in front of the waveform `wv` and extends (or cuts off) the waveform at the end with the last value of `wv`. A waveform of length `total_waveform_length` is returned.

## Arguments

  * `wv::RadiationDetectorSignals.RDWaveform{T,U,TV,UV}`: A waveform (signal over time).
  * `n_baseline_samples::Int`: Number of samples added in front of the waveform with values 0.
  * `total_waveform_length::Int`: Number of samples of the extended waveform which is returned.

## Examples

```
add_baseline_and_extend_tail(wv, 1000, 5000)
```

!!! note
    This functions assumes that the time steps between the samples of the input waveform `wv` are the same. Thus, that the input waveform is sampled with a fixed frequency.

