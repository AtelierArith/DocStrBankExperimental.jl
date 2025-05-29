```
get_noise_error(d::Design, noise_est::NoiseEstimate)
get_noise_error(d_rand::RandDesign, noise_est::NoiseEstimate)
```

Returns a [`NoiseError`](@ref) object containing the normalised root-mean-square errors (NRMSEs) for the gate noise estimates in `noise_est` and the true gate eigenvalues for the design `d`, or alternatively the randomised design `d_rand`.
