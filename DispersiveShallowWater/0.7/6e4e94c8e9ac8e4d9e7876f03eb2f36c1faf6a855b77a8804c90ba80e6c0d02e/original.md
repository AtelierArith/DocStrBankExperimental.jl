```
energy_total(q, equations)
```

Return the total energy of the primitive variables `q` for a given set of `equations`. For all [`AbstractShallowWaterEquations`](@ref), the total energy is given by the sum of the kinetic and potential energy of the shallow water subsystem, i.e.,

$$
\frac{1}{2} h v^2 + \frac{1}{2} g \eta^2
$$

in 1D, where $h$ is the [`waterheight`](@ref), $\eta = h + b$ the [`waterheight_total`](@ref), $v$ the [`velocity`](@ref), and $g$ the [`gravity`](@ref).

`q` is a vector of the primitive variables at a single node, i.e., a vector of the correct length `nvariables(equations)`.
