```
interpolation_setup(;Γ,lon,lat,path,url)
```

Download or recompute interpolation coefficients.

  * `λ=interpolation_setup()` to download "interp*coeffs*halfdeg.jld2"
  * `λ=interpolation_setup(Γ=Γ)` to recompute interpolation to `lon,lat`
