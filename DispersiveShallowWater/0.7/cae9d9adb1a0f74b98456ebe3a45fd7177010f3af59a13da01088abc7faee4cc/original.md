```
EulerEquations1D(; gravity, eta0 = 0.0)
```

A struct representing the 1D Euler equations with a given gravitational acceleration `gravity` and a still-water surface `eta0`.

!!! note
    In DispersiveShallowWater.jl, the Euler equations are *only* used for computing the full linear dispersion relation

    $$
    \omega(k) = \sqrt{g k \tanh(h_0 k)},
    $$

    see [`LinearDispersionRelation`](@ref) and [`wave_speed`](@ref). The `EulerEquations1D` cannot be solved as a system of equations.

