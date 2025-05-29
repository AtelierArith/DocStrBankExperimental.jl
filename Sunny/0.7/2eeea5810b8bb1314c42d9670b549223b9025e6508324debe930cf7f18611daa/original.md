```
propose_uniform
```

Function to propose a uniformly random spin update in the context of a [`LocalSampler`](@ref). In `:dipole` mode, the result is a random three-vector with appropriate normalization. In `:SUN` mode, the result is a random SU(*N*) coherent state with appropriate normalization.

For low-temperature Monte Carlo simulations, uniform spin proposals can be very inefficient due to a high probability of rejection in the Metropolis accept/reject step. Consider also [`Langevin`](@ref) sampling, which is rejection free.
