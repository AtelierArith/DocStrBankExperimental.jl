```julia
acquire(
    system,
    signal,
    sampling_freq,
    prns;
    interm_freq,
    max_doppler,
    dopplers
)

```

Perform the aquisition of multiple satellites with `prns` in system `system` with signal `signal` sampled at rate `sampling_freq`. Optional arguments are the intermediate frequency `interm_freq` (default 0Hz), the maximum expected Doppler `max_doppler` (default 7000Hz). If the maximum Doppler is too unspecific you can instead pass a Doppler range with with your individual step size using the argument `dopplers`.
