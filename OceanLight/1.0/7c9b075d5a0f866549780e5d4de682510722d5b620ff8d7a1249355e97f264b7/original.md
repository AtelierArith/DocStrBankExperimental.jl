```
convertwave!(η, ηx, ηy, η0, ηx0, ηy0, kbc)
```

Convert the surface wave geometry `η0`, `ηx0`, `ηy0` to  `η`, `ηx`, `ηy` with the same size as irradiance field.  Can be used for nonperiodic BC`kbc=1` (no interpolation) or periodic BC `kbc=0` (interpolation using FFT)
