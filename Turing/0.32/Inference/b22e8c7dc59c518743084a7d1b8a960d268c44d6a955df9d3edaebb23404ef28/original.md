```
SGLD(
    space::Symbol...;
    stepsize = PolynomialStepsize(0.01),
    adtype::ADTypes.AbstractADType = AutoForwardDiff(),
)
```

Stochastic gradient Langevin dynamics (SGLD) sampler.

By default, a polynomially decaying stepsize is used.

If the automatic differentiation (AD) backend `adtype` is not provided, ForwardDiff with automatically determined `chunksize` is used.

# Reference

Max Welling & Yee Whye Teh (2011). Bayesian Learning via Stochastic Gradient Langevin Dynamics. In: Proceedings of the 28th International Conference on Machine Learning (pp. 681–688).

See also: [`PolynomialStepsize`](@ref)
