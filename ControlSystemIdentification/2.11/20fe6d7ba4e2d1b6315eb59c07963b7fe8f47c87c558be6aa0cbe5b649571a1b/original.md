```
Gtf = arx(d::AbstractIdData, na, nb; inputdelay = ones(Int, size(nb)), λ = 0, estimator=\, stochastic=false)
```

Fit a transfer Function to data using an ARX model and equation error minimization.

The ARX abbreviation is for "AutoRegressive model with eXogenous input".

  * `nb` and `na` are the number of coefficients of the numerator and denominator polynomials, respectively.

Input delay can be added via `inputdelay = d`, which corresponds to an additional delay of `z^-d`. An `inputdelay = 0` results in a direct term. The highest order of the B polynomial is given by `nb + inputdelay - 1`.  `λ > 0` can be provided for L₂ regularization. `estimator` defaults to \ (least squares), alternatives are `estimator = tls` for total least-squares estimation.  `arx(Δt,yn,u,na,nb, estimator=wtls_estimator(y,na,nb)` is potentially more robust in the presence of heavy measurement noise. The number of free parameters is `na+nb` 

  * `stochastic`: if true, returns a transfer function with uncertain parameters represented by `MonteCarloMeasurements.Particles`.

Supports MISO estimation by supplying an iddata with a matrix `u`, with nb = [nb₁, nb₂...] and optional inputdelay = [d₁, d₂...]

This function supports multiple datasets, provided as a vector of iddata objects.
