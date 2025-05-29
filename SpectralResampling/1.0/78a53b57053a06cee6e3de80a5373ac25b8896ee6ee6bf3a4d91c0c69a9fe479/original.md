```
get_logarithmic_λ(λ[, log_spacing])
```

Calculate a logarithmically-spaced wavelength grid given a linearly spaced wavelength grid `λ`, optionally specifying the spacing (in log space) between elements `log_spacing`. For example, if `lnλ` is a logarithmically spaced wavelength grid, the `log_spacing` would be defined as `log_spacing = log(lnλ[2]/lnλ[1]) = log(lnλ[end]/lnλ[end-1])`.
