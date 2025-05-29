```
P = covar(sys, W)
```

Calculate the stationary covariance `P = E[y(t)y(t)']` of the output `y` of a `StateSpace` model `sys` driven by white Gaussian noise `w` with covariance `E[w(t)w(τ)]=W*δ(t-τ)` (δ is the Dirac delta).

Remark: If `sys` is unstable then the resulting covariance is a matrix of `Inf`s. Entries corresponding to direct feedthrough (D*W*D' .!= 0) will equal `Inf` for continuous-time systems.

See also [`innovation_form`](@ref).
