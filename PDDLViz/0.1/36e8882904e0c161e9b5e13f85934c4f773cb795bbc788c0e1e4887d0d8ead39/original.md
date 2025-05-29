```
anim_transition!(canvas, renderer, domain, state, [action, t];
                 callback=nothing, overlay=nothing, kwargs...)
```

Animates a transition from the current state stored in the `canvas` to the newly provided `state` (via `action` at timestep `t` if provided). Called by [`anim_plan`](@ref) and [`anim_trajectory`](@ref) to animate a series of state transitions.

By default, this updates the `canvas` with the new `state`, then runs the `overlay` and `callback` functions (if provided) on `canvas` (e.g. to ovelay annotations, or to record a frame).

This function can be overloaded for different [`Renderer`](@ref) types to implement custom transitions, e.g., transitions that involve multiple frames. 
