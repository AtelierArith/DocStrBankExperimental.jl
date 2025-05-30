```
interpolation_setup(;Γ,lon,lat,path,url)
```

補間係数をダウンロードまたは再計算します。

  * `λ=interpolation_setup()` は "interp*coeffs*halfdeg.jld2" をダウンロードします
  * `λ=interpolation_setup(Γ=Γ)` は `lon,lat` への補間を再計算します
