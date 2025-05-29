```
fourier_attenuation(f::Vector{S}, r::T, ane::AnelasticAttenuationParameters{U,V}, site::SiteParameters{W}) where {S<:Float64,T<:Real,U<:Real,V<:Real,W<:Real}
```

Combined full-path attenuation, including `Q(f)` effects and `κ0` filter for frequency `f` Distance defined in terms of an equivalent point source distance `r_ps` or rupture distance `r_rup` depending upon what metric is defined in `ane.rmetric`
