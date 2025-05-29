```julia
get_correlator_sample_shifts(
    system,
    correlator,
    sampling_frequency,
    preferred_code_shift
)

```

Calculate the replica phase offset required for the correlator with respect to the prompt correlator, expressed in samples. The shifts are ordered from latest to earliest replica.
