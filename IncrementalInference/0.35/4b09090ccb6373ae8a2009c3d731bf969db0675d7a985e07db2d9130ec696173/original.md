```julia
approxDeconv(dfg, fctsym; ...)
approxDeconv(dfg, fctsym, solveKey; retries)

```

Generalized deconvolution to find the predicted measurement values of the factor `fctsym` in `dfg`. Inverse solve of predicted noise value and returns tuple of (newly predicted, and known "measured" noise) values.

Notes

  * Opposite operation contained in `approxConvBelief`.
  * For more notes see [`solveFactorMeasurements`](@ref).

Related

[`approxConvBelief`](@ref), `deconvSolveKey`
