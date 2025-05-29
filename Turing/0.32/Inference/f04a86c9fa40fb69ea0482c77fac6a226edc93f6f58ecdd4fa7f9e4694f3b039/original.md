```
HMCDA(
    n_adapts::Int, δ::Float64, λ::Float64; ϵ::Float64 = 0.0;
    adtype::ADTypes.AbstractADType = AutoForwardDiff(),
)
```

Hamiltonian Monte Carlo sampler with Dual Averaging algorithm.

# Usage

```julia
HMCDA(200, 0.65, 0.3)
```

# Arguments

  * `n_adapts`: Numbers of samples to use for adaptation.
  * `δ`: Target acceptance rate. 65% is often recommended.
  * `λ`: Target leapfrog length.
  * `ϵ`: Initial step size; 0 means automatically search by Turing.
  * `adtype`: The automatic differentiation (AD) backend.   If not specified, `ForwardDiff` is used, with its `chunksize` automatically determined.

# Reference

For more information, please view the following paper ([arXiv link](https://arxiv.org/abs/1111.4246)):

Hoffman, Matthew D., and Andrew Gelman. "The No-U-turn sampler: adaptively setting path lengths in Hamiltonian Monte Carlo." Journal of Machine Learning Research 15, no. 1 (2014): 1593-1623.
