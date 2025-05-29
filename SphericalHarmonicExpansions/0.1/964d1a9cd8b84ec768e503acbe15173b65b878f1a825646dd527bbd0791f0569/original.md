```
translation(C::SphericalHarmonicCoefficients,v::Array{Float64,1})
```

*Description:* Translation of the coefficients: Shifting the expansion point by v

*Input:*

  * `C`  - Coefficients
  * `v`  - shift vector (length(v) = 3)

*Output:*

  * `cT` - Translated coefficients, type: SphericalHarmonicCoefficients (cT.R = C.R, cT.solid = C.solid)
