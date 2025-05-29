```julia
R2BSystem(; stm, name, defaults, kwargs...)

```

A `ModelingToolkit.ODESystem` for the Restricted Two-body Problem.

The order of the states follows: `[x, y, z, ẋ, ẏ, ż]`.

The order of the parameters follows: `[μ]`.

# Extended Help

The Restricted Two-body Problem is a simplified dynamical model describing one small body (spacecraft, etc.) and one celestial body. The gravity of the celestial body exhibits a force on the small body. This model is commonly used as a simplification to descibe our solar systems' planets orbiting our sun, or a spacecraft orbiting Earth.

### Usage

```julia
model = R2BSystem()
```
