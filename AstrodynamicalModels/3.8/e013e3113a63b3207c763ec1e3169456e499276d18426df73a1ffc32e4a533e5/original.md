```julia
CR3BSystem(; stm, name, defaults, kwargs...)

```

A `ModelingToolkit.ODESystem` for the Circular Restricted Three-body Problem.

The order of the states follows: `[x, y, z, ẋ, ẏ, ż]`.

The order of the parameters follows: `[μ]`.

# Extended Help

The Circular Restricted Three-body Problem is a simplified dynamical model describing one small body (spacecraft, etc.) and two celestial bodies moving in a circle about their common center of mass. This may seem like an arbitrary simplification, but this assumption holds reasonably well for the Earth-Moon, Sun-Earth, and many other systems in our solar system.

### Usage

```julia
model = CR3BSystem(; stm=true)
```
