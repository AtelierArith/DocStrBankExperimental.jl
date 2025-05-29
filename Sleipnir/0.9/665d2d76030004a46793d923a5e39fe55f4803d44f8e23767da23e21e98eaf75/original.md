Initialize the physical parameters of a model.

```
PhysicalParameters(;
    ρ::Float64 = 900.0,
    g::Float64 = 9.81,
    ϵ::Float64 = 1e-3,
    η₀::F = 1.0, 
    maxA::Float64 = 8e-17,
    minA::Float64 = 8.5e-20,
    maxTlaw::Float64 = 1.0,
    minTlaw::Float64 = -25.0,
    noise_A_magnitude::Float64 = 5e-18
    )
```

# Keyword arguments

```
- `ρ`: Ice density
- `g`: Gravitational constant
- `ϵ`: Small number
- `η₀`:  
- `maxA`: Maximum value for `A` (Glen's coefficient)
- `minA`: Minimum value for `A` (Glen's coefficient)
- `maxTlaw`: Maximum value of Temperature used in simulations on fake law
- `minTlaw`: Minimum value of Temperature used in simulations on fake law
- `noise_A_magnitude`: Magnitude of noise added to A
```
