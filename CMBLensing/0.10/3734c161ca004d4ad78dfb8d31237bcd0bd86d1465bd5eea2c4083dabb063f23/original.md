```
ud_grade(f::Field, θnew, mode=:map, deconv_pixwin=true, anti_aliasing=true)
```

Up- or down-grades field `f` to new resolution `θnew` (only in integer steps). Two modes are available specified by the `mode` argument: 

  * `:map`     — Up/downgrade by replicating/averaging pixels in map-space
  * `:fourier` — Up/downgrade by extending/truncating the Fourier grid

For `:map` mode, two additional options are possible. If `deconv_pixwin` is true, deconvolves the pixel window function from the downgraded map so the spectrum of the new and old maps are the same. If `anti_aliasing` is true, filters out frequencies above Nyquist prior to down-sampling. 
