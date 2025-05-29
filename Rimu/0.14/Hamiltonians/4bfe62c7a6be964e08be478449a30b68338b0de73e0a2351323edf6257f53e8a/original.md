```
G2RealCorrelator(d::Int) <: AbstractOperator{Float64}
```

Two-body operator for density-density correlation between sites separated by `d` with `0 ≤ d < M`.

$$
    \hat{G}^{(2)}(d) = \frac{1}{M} \sum_i^M \hat{n}_i (\hat{n}_{i+d} - \delta_{0d}).
$$

Assumes a one-dimensional lattice with periodic boundary conditions where

$$
    \hat{G}^{(2)}(-M/2 \leq d < 0) = \hat{G}^{(2)}(|d|),
$$

$$
    \hat{G}^{(2)}(M/2 < d < M) = \hat{G}^{(2)}(M - d),
$$

and normalisation

$$
    \sum_{d=0}^{M-1} \langle \hat{G}^{(2)}(d) \rangle = \frac{N (N-1)}{M}.
$$

For multicomponent basis, calculates correlations between all particles equally, equivalent to stacking all components into a single Fock state.

# Arguments

  * `d::Integer`: distance between sites.

# See also

  * [`HubbardReal1D`](@ref)
  * [`G2RealSpace`](@ref)
  * [`G2MomCorrelator`](@ref)
  * [`AbstractOperator`](@ref)
  * [`AllOverlaps`](@ref)
