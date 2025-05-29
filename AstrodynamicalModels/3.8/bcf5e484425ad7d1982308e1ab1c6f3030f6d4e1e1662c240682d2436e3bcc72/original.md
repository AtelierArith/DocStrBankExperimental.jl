```julia
NBSystem(N; stm, name, defaults, kwargs...)

```

A `ModelingToolkit.ODESystem` for the Newtonian N-body Problem.

The order of the states follows: `[x₁, y₁, z₁, ..., xₙ, yₙ, zₙ, ẋ₁, ẏ₁, ż₁, ..., ẋₙ, ẏₙ, żₙ]`.

The order of the parameters follows: `[G, m₁, m₂, ..., mₙ]`.

!!! warning
    Be careful about specifying `stm=true` for systems with `N ≥ 3`! If state transition matrix dynamics are enabled, you can calculate the total number of system states with `N*6 + (N*6)^2`. Note that this increases exponentially as `N` grows! For `N == 6`, unless you're using parallelization, your computer may run for several hours.


# Extended Help

The N-body problem is a model which describes how `N` bodies will move with respect to a common origin. This problem typically involves many bodies which act due to one force: electromagentism, gravity, etc. This model applies most closely to many celestial bodies moving due to gravity. That's about right for a model in a package called `AstrodynamicalModels`!

### Usage

```julia
# One model for ALL the planets in our solar system 😎
model = NBSystem(9)
```
