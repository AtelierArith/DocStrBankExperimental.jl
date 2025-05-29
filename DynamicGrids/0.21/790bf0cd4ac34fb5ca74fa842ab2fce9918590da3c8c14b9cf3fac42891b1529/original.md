```
Frame <: AbstractDelay

Frame{K}(frame)
```

`Frame` allows using a [`Grid`](@ref) from a specific previous timestep from within a rule, using `get`. It should only be used within rule code, not as a parameter.

# Type Parameter

  * `K::Symbol`: matching the name of a grid in `init`.

# Argument

  * `frame::Int`: the exact frame number to use.

WARNING: This feature is experimental. It may change in future versions,  and may not be 100% reliable in all cases. Please file github issues if problems occur.
