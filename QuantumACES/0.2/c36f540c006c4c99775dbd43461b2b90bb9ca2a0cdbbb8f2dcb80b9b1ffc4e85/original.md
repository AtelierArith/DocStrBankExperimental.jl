```
get_aic(d::Design, noise_est::NoiseEstimate; projected::Bool = false)
get_aic(d_rand::RandDesign, noise_est::NoiseEstimate; projected::Bool = false)
```

Returns the Akaike information criterion (AIC) corresponding to the noise estimate `noise_est`, given the design `d` or alternatively the randomised design `d_rand`, calculating with the projected gate eigenvalues if `projected` is `true`.
