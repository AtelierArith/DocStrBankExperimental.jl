```
get_noise_score(noise_error::NoiseError, merit::Merit)
get_noise_score(noise_error_vector::Vector{NoiseError}, merit::Merit)
get_noise_score(noise_error_matrix::Matrix{NoiseError}, merit::Merit)
```

Returns a [`NoiseScore`](@ref) object containing the z-scores for the supplied normalised root-mean-square error (NRMSE) data in `noise_error` given the merit `merit`.
