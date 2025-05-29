```
LogBayesQuad(k::Kernel; n_candidates=100, l=1.0, σ::Real=1.0)
```

Tool for running Bayesian Quadrature by assuming a GP on the log integrand instead of the integrand.

## Arguments

  * `n_candidates` : will be sampled around the first samples to perform a linear approximation of the result.
  * `l` : Lengthscale of the kernel
  * `σ` : variance of the kernel

## Reference

  * **Active Learning of Model Evidence Using Bayesian Quadrature** - Osborne et al. - NIPS 2012.
