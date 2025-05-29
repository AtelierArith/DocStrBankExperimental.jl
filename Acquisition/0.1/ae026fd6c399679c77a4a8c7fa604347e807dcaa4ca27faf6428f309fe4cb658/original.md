```julia
coarse_fine_acquire(
    system,
    signal,
    sampling_freq,
    prns;
    interm_freq,
    max_doppler,
    coarse_step,
    fine_step
)

```

Performs a coarse aquisition and fine acquisition of multiple satellites `prns` in system `system` with signal `signal` sampled at rate `sampling_freq`. The aquisition is performed as parallel code phase search using the Doppler frequencies with coarse step size `coarse_step` and fine step size `fine_step`.
