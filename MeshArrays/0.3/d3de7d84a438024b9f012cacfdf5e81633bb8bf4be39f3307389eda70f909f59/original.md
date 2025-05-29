```
interpolation_setup(;Γ,lon,lat,filename)
```

Download or recompute interpolation coefficients.

  * `λ=interpolation_setup()` to download "interp*coeffs*halfdeg.jld2"
  * `λ=interpolation_setup(Γ=Γ)` to recompute interpolation to `lon,lat`
  * `λ=interpolation_setup(Γ=Γ,lon=lon,lat=lat,filename=filename)` to    recompute interpolation to `lon,lat` and save to location and file `filename`,   defaulting to `tempname()*"_interp_coeffs.jld2"`.
