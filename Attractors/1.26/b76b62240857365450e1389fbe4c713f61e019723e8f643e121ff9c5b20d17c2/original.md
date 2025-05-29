```
uncertainty_exponent(basins; kwargs...) -> ε, N_ε, α
```

Estimate the uncertainty exponent[Grebogi1983](@cite) of the basins of attraction. This exponent is related to the final state sensitivity of the trajectories in the phase space. An exponent close to `1` means basins with smooth boundaries whereas an exponent close to `0` represent completely fractalized basins, also called riddled basins.

The output `N_ε` is a vector with the number of the balls of radius `ε` (in pixels) that contain at least two initial conditions that lead to different attractors. The output `α` is the estimation of the uncertainty exponent using the box-counting dimension of the boundary by fitting a line in the `log.(N_ε)` vs `log.(1/ε)` curve. However it is recommended to analyze the curve directly for more accuracy.

## Keyword arguments

  * `range_ε = 2:maximum(size(basins))÷20` is the range of sizes of the ball to test (in pixels).

## Description

A phase space with a fractal boundary may cause a uncertainty on the final state of the dynamical system for a given initial condition. A measure of this final state sensitivity is the uncertainty exponent. The algorithm probes the basin of attraction with balls of size `ε` at random. If there are a least two initial conditions that lead to different attractors, a ball is tagged "uncertain". `f_ε` is the fraction of "uncertain balls" to the total number of tries in the basin. In analogy to the fractal dimension, there is a scaling law between, `f_ε ~ ε^α`. The number that characterizes this scaling is called the uncertainty exponent `α`.

Notice that the uncertainty exponent and the box counting dimension of the boundary are related. We have `Δ₀ = D - α` where `Δ₀` is the box counting dimension computed with [`basins_fractal_dimension`](@ref) and `D` is the dimension of the phase space. The algorithm first estimates the box counting dimension of the boundary and returns the uncertainty exponent.
