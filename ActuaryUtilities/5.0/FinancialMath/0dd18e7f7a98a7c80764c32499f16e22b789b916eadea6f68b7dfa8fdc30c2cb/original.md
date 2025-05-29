```
KeyRate(timepoints,shift=0.001)
```

A convenience constructor for [`KeyRateZero`](@ref). 

## Extended Help

[`KeyRateZero`](@ref) is chosen as the default constructor because it has more attractive properties than [`KeyRatePar`](@ref):

  * rates after the key `timepoint` remain unaffected by the `shift`

      * e.g. this causes a 6-year zero coupon bond would have a negative duration if the 5-year par rate was used
