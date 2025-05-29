```
SGHMC(
    space::Symbol...;
    learning_rate::Real,
    momentum_decay::Real,
    adtype::ADTypes.AbstractADType = AutoForwardDiff(),
)
```

Create a Stochastic Gradient Hamiltonian Monte Carlo (SGHMC) sampler.

If the automatic differentiation (AD) backend `adtype` is not provided, ForwardDiff with automatically determined `chunksize` is used.

# Reference

Tianqi Chen, Emily Fox, & Carlos Guestrin (2014). Stochastic Gradient Hamiltonian Monte Carlo. In: Proceedings of the 31st International Conference on Machine Learning (pp. 1683–1691).
