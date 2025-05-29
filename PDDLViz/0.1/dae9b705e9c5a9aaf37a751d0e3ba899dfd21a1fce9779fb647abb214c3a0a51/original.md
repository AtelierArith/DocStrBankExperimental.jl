```
anim_initialize!(canvas, renderer, domain, state;
                 callback=nothing, overlay=nothing, kwargs...)
```

Initializes an animation that will be rendered on the `canvas`. Called by [`anim_plan`](@ref) and [`anim_trajectory`](@ref) as an initialization step.

By default, this just renders the initial `state` on the `canvas`. This function can be overloaded for different [`Renderer`](@ref) types to implement custom initializations, e.g., to add captions or other overlays.
