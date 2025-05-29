```
pmrand(::Type{PM}, n, m[, period = 2pi]; nh = 1) 
pmrand(::Type{PM{:c,T}}, n, m[, period = 2pi]; nh = 1) 
pmrand(n, m[, period = 2pi]; nh = 1) 
pmrand(PeriodicTimeSeriesMatrix, n, m[, period = 2pi]; ns = 1) 
pmrand(PeriodicTimeSeriesMatrix{:c,T}, n, m[, period = 2pi]; ns = 1) 
pmrand(PeriodicSwitchingMatrix, n, m[, period = 2pi]; ts = [0]) 
pmrand(PeriodicSwitchingMatrix{:c,T}, n, m[, period = 2pi]; ts = [0])
```

Generate a random `n×m` continuous-time periodic matrix of type `PM` or `PM{:c,T}` with period  `period` (default:  `period = 2pi`). `PM` specifies the resulting type of the generated periodic matrix. For `PM = HarmonicArray`, or `PM = PeriodicFunctionMatrix`, or `PM = PeriodicSymbolicMatrix` or `PM = FourierFunctionMatrix`, the resulting periodic matrix corresponds  to a random harmonic representation with  `nh` harmonic components (default:  `nh = 1`).  The type  `T` of matrix elements can be specified using, e.g. `HarmonicArray{:c,T}` instead `HarmonicArray`,  which assumes by default `T = Float64`. If `PM` is omitted, then by default `PM = HarmonicArray`.

For `PM = PeriodicTimeSeriesMatrix`, `ns` specifies the number of component matrices.

For `PM = PeriodicSwitchingMatrix`, the vector `ts` specifies the switching times. 
