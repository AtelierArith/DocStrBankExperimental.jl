```
τ, acf = autocov(t::AbstractVector, y::AbstractVector{T}, maxlag; normalize=false) where T <: Number
```

Calculate the autocovariance function for a signal `y` sampled at sample times `t`. This is useful if the signal is sampled non-equidistantly.

If `y` and `t` are vectors of vectors, the acf for all data is estimated and concatenated in the output, which is always two vectors of numbers.

The returned vectors are samples of the acf at lags `τ`. `τ` contains differences between entries in `t`, whereas `lags` supplied to the standard metohd of `autocov` are the differences between *indices* in `y` to compare. The result will in general be noisier that the stadard `autocov` and may require further estimation, e.g., by means of gaussian process regression or quantile regression. The following should hold `mean(acf[τ.==0]) ≈ var(y)`.

#Arguments:

  * `t`: Vector of sample locations/times
  * `y`: signal
  * `maxlag`: Specifies the maximum difference between two values in `t` for which to calculate the ACF
  * `normalize`: If false (default) the behaviour mimics the standard method from StatsBase and the ACF decreases automatically for higher lags, even if the theoretical ACF does not. If `true`, the theoretical ACF is estimated. `normalize = true` leads to sharper spectral estimates when taking the fft of the ACF. Note that the variance in the estimated ACF will be high for large lags if `true`.
