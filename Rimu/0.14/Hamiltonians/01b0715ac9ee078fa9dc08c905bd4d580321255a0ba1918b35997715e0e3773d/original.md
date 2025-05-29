```
SuperfluidCorrelator(d::Int) <: AbstractOperator{Float64}
```

Operator for extracting superfluid correlation between sites separated by a distance `d` with `0 ≤ d < M`:

$$
    \hat{C}_{\text{SF}}(d) = \frac{1}{M} \sum_{i}^{M} a_{i}^{\dagger} a_{i + d}
$$

Assumes a one-dimensional lattice with $M$ sites and periodic boundary conditions. $M$ is also the number of modes in the Fock state address.

# Usage

Superfluid correlations can be extracted from a Monte Carlo calculation by wrapping `SuperfluidCorrelator` with [`AllOverlaps`](@ref) and passing into [`ProjectorMonteCarloProblem`](@ref) with the `replica` keyword argument. For an example with a similar use of [`G2RealCorrelator`](@ref) see [G2 Correlator Example](https://RimuQMC.github.io/Rimu.jl/previews/PR227/generated/G2-example.html).

See also [`HubbardReal1D`](@ref), [`G2RealCorrelator`](@ref), [`AbstractOperator`](@ref), and [`AllOverlaps`](@ref).
