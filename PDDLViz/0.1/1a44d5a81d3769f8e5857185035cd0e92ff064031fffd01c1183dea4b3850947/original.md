```
render_trajectory(renderer::Renderer,
                  domain::Domain, trajectory::AbstractVector{<:State})
```

Uses `renderer` to render a `trajectory` of PDDL `domain` states. Constructs and returns a new [`Canvas`](@ref).
