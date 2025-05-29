```
mapspectra(f, echogram[; freqdim, distributed])
```

Map the function `f` over each spectrum in the `DimArray` `echogram`. By default assumes the acoustic frequencies are recorded in dimension `:F`, if this is not the case, specify the name of the dimension using the `freqdim` argument.
