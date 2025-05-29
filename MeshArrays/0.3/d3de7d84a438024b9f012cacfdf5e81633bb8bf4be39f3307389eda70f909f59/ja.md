```
interpolation_setup(;Γ,lon,lat,filename)
```

補間係数をダウンロードまたは再計算します。

  * `λ=interpolation_setup()` は "interp*coeffs*halfdeg.jld2" をダウンロードします
  * `λ=interpolation_setup(Γ=Γ)` は `lon,lat` への補間を再計算します
  * `λ=interpolation_setup(Γ=Γ,lon=lon,lat=lat,filename=filename)` は `lon,lat` への補間を再計算し、場所とファイル `filename` に保存します。デフォルトは `tempname()*"_interp_coeffs.jld2"` です。
