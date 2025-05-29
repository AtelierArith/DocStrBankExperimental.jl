```
get_bic(d::Design, noise_est::NoiseEstimate; projected::Bool = false)
get_bic(d_rand::RandDesign, noise_est::NoiseEstimate; projected::Bool = false)
```

Returns the Bayesian information criterion (BIC) corresponding to the noise estimate `noise_est`, given the design `d` or alternatively the randomised design `d_rand`, calculating with the projected gate eigenvalues if `projected` is `true`.
