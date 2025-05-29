```julia
AttitudeSystem(; stm, name, defaults, kwargs...)

```

A `ModelingToolkit.ODESystem` for atmospheric entry. Currently, only exponential atmosphere models are provided! The output model is cached with `Memoize.jl`. Planet-specific parameters default to Earth values.

The order of the states follows: `[q₁, q₂, q₃, q₄, ω₁, ω₂, ω₃]`.

The order of the parameters follows: `[]`

# Extended Help

This model describes how an object moves through an exponential atmosphere, above a spherical planet.

## States

1. `q`: scalar-last attitude quaternion
2. `ω`: body rates (radians per second)

## Parameters

1. `J`: inertial matrix
2. `L`: lever arm where input torque is applied
3. `f`: torques on the vehicle body (Newton-meters)

### Usage

```julia
model = Attitude()
```
