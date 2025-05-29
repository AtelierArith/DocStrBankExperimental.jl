```
combined_kappa_frequency(r::T, Af2target::Float64, ane::AnelasticAttenuationParameters, site::SiteParameters) where T<:Real
```

Frequency at which the combined κ*r and κ*0 filters (squared versions) give a value of `Af2target`. `r` can be either `r_ps` or `r_rup` depending upon what matches `ane.rmetric`
