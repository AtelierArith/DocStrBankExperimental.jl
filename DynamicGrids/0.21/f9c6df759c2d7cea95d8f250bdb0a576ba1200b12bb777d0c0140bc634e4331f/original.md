```
Delay <: AbstractDelay

Delay{K}(steps)
```

`Delay` allows using a [`Grid`](@ref) from previous timesteps as a parameter source as a field in any `Rule` that uses `get` to retrieve it's parameters.

It must be coupled with an output that stores all frames, so that `@assert DynamicGrids.isstored(output) == true`.  With [`GraphicOutput`](@ref)s this may be acheived by using the keyword argument `store=true` when constructing the output object.

# Type Parameters

  * `K::Symbol`: matching the name of a grid in `init`.

# Arguments

  * `steps`: As a user supplied parameter, this is a multiple of the step size of the output   `tspan`. This is automatically replaced with an integer for each step. Used within the   code in a rule, it must be an `Int` number of frames, for performance.

# Example

```julia
SomeRule(;
    someparam=Delay(:grid_a, Month(3))
    otherparam=1.075
)
```

WARNING: This feature is experimental. It may change in future versions,  and may not be 100% reliable in all cases. Please file github issues if problems occur.
