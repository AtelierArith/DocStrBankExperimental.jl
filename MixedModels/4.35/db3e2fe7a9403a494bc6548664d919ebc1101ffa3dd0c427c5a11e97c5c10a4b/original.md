```
GeneralizedLinearMixedModel
```

Generalized linear mixed-effects model representation

# Fields

  * `LMM`: a [`LinearMixedModel`](@ref) - the local approximation to the GLMM.
  * `β`: the pivoted and possibly truncated fixed-effects vector
  * `β₀`: similar to `β`. Used in the PIRLS algorithm if step-halving is needed.
  * `θ`: covariance parameter vector
  * `b`: similar to `u`, equivalent to `broadcast!(*, b, LMM.Λ, u)`
  * `u`: a vector of matrices of random effects
  * `u₀`: similar to `u`.  Used in the PIRLS algorithm if step-halving is needed.
  * `resp`: a `GlmResp` object
  * `η`: the linear predictor
  * `wt`: vector of prior case weights, a value of `T[]` indicates equal weights.

The following fields are used in adaptive Gauss-Hermite quadrature, which applies only to models with a single random-effects term, in which case their lengths are the number of levels in the grouping factor for that term.  Otherwise they are zero-length vectors.

  * `devc`: vector of deviance components
  * `devc0`: vector of deviance components at offset of zero
  * `sd`: approximate standard deviation of the conditional density
  * `mult`: multiplier

# Properties

In addition to the fieldnames, the following names are also accessible through the `.` extractor

  * `theta`: synonym for `θ`
  * `beta`: synonym for `β`
  * `σ` or `sigma`: common scale parameter (value is `NaN` for distributions without a scale parameter)
  * `lowerbd`: vector of lower bounds on the combined elements of `β` and `θ`
  * `formula`, `trms`, `A`, `L`, and `optsum`: fields of the `LMM` field
  * `X`: fixed-effects model matrix
  * `y`: response vector
