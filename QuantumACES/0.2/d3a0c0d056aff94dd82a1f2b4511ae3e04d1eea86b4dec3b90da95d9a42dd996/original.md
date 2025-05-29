```
get_model_violation(d::Design, noise_est::NoiseEstimate; projected::Bool = false)
get_model_violation(d_rand::RandDesign, noise_est::NoiseEstimate; projected::Bool = false)
get_model_violation(d::Design, noise_est_vector::Vector{NoiseEstimate}; projected::Bool = false)
get_model_violation(d::Design, noise_est_matrix::Matrix{NoiseEstimate}; projected::Bool = false)
```

Returns the noise model violation z-score for the generalised residual sum of squares corresponding to the noise estimate `noise_est`, given the design `d` or alternatively the randomised design `d_rand`, calculating with the projected gate eigenvalues if `projected` is `true`.
