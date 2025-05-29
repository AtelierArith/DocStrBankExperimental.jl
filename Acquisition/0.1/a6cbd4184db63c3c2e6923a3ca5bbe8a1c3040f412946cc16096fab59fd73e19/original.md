```julia
acquire!(
    acq_plan,
    signal,
    prns;
    interm_freq,
    doppler_offset,
    noise_power
)

```

This acquisition function uses a predefined acquisition plan to accelerate the computing time. This will be useful, if you have to calculate the acquisition multiple time in a row.
