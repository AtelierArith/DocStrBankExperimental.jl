```
get_rss(d::Design, noise_est::NoiseEstimate; projected::Bool = false)
get_rss(d_rand::RandDesign, noise_est::NoiseEstimate; projected::Bool = false)
```

Returns the generalised residual sum of squares corresponding to the noise estimate `noise_est`, given the design `d` or alternatively the randomised design `d_rand`, calculating with the projected gate eigenvalues if `projected` is `true`.
