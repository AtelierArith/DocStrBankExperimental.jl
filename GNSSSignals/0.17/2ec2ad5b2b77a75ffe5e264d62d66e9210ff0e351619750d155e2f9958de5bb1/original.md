```julia
gen_code(num_samples, gnss, prn, sampling_frequency)
gen_code(
    num_samples,
    gnss,
    prn,
    sampling_frequency,
    code_frequency
)
gen_code(
    num_samples,
    gnss,
    prn,
    sampling_frequency,
    code_frequency,
    start_phase
)
gen_code(
    num_samples,
    gnss,
    prn,
    sampling_frequency,
    code_frequency,
    start_phase,
    start_index
)

```

Generate the code signal for PRN-Number `prn` of system `gnss` at chip rate `code_frequency`, sampled at sampling rate `sampling_frequency`. Make sure, that `sampling_frequency` is larger than `code_frequency` to avoid overflows with the modulo calculation.
