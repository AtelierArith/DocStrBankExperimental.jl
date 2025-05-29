```
render_trajectory!(canvas::Canvas, renderer::Renderer,
                   domain::Domain, trajectory::AbstractVector{<:State})
```

Uses `renderer` to render a `trajectory` of PDDL `domain` states. Renders to a `canvas` on top of any existing content.
