```
mt_ccvf(S; <keyword arguments>)
```

Computes univariate multitaper cross-covariance/cross-correlation function. Inputs a MTSpectrum struct.

...

# Arguments

  * `S::MTSpectrum`: the vector containing the result of an multiivariate call to `multispec`
  * `typ::Symbol = :ccvf`: whether to compute cross-correlation function (:ccf) or cross-covariance function (:ccvf)

...

...

# Outputs

  * `MtCrossCovarianceFunction`, `MTCrossCorrelationFunction` depending on the selection of `typ` input above.

...

See also: [`multispec`](@ref)
