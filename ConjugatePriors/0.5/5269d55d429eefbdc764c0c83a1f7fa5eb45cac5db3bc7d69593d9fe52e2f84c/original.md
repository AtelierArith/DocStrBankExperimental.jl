```
NormalInverseChisq(μ, σ2, κ, ν)
```

A Normal-χ^-2 distribution is a conjugate prior for a Normal distribution with unknown mean and variance.  It has parameters:

  * μ: expected mean
  * σ2 > 0: expected variance
  * κ ≥ 0: mean confidence
  * ν ≥ 0: variance confidence

The parameters have a natural interpretation when used as a prior for a Normal distribution with unknown mean and variance: μ and σ2 are the expected mean and variance, while κ and ν are the respective degrees of confidence (expressed in "pseudocounts").  When interpretable parameters are important, this makes it a slightly more convenient parametrization of the conjugate prior.

Equivalent to a `NormalInverseGamma` distribution with parameters:

  * m0 = μ
  * v0 = 1/κ
  * shape = ν/2
  * scale = νσ2/2

Based on Murphy "Conjugate Bayesian analysis of the Gaussian distribution".
