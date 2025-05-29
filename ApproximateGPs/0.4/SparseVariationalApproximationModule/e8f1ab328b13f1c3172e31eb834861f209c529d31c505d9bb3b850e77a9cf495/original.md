```
elbo(
    sva::SparseVariationalApproximation,
    fx::FiniteGP,
    y::AbstractVector{<:Real};
    num_data=length(y),
    quadrature=GPLikelihoods.DefaultExpectationMethod(),
)
```

Compute the Evidence Lower BOund from [1] for the process `f = fx.f == svgp.fz.f` where `y` are observations of `fx`, pseudo-inputs are given by `z = svgp.fz.x` and `q(u)` is a variational distribution over inducing points `u = f(z)`.

`quadrature` is passed on to `GPLikelihoods.expected_loglikelihood` and selects which method is used to calculate the expected loglikelihood in the ELBO. See `GPLikelihoods.expected_loglikelihood` for more details.

N.B. the likelihood is assumed to be Gaussian with observation noise `fx.Σy`. Further, `fx.Σy` must be isotropic - i.e. `fx.Σy = σ² * I`.

[1] - Hensman, James, Alexander Matthews, and Zoubin Ghahramani. "Scalable variational Gaussian process classification." Artificial Intelligence and Statistics. PMLR, 2015.
