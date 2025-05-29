```
Lag <: AbstractDelay

Lag{K}(frames::Int)
```

`Lag` allows using a [`Grid`](@ref) from a specific previous frame from within a rule, using `get`. It is similar to [`Delay`](@ref), but an integer amount of frames should be used, instead of a quantity related to the simulation `tspan`. The lower bound is the first frame.

# Type Parameter

  * `K::Symbol`: matching the name of a grid in `init`.

# Argument

  * `frames::Int`: number of frames to lag by, 1 or larger.

# Example

```julia
SomeRule(;
    someparam=Lag(:grid_a, Month(3))
    otherparam=1.075
)
```

WARNING: This feature is experimental. It may change in future versions,  and may not be 100% reliable in all cases. Please file github issues if problems occur.
