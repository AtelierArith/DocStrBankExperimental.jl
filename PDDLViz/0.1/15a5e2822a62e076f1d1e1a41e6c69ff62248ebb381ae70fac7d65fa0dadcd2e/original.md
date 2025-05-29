```
render_sol(renderer::Renderer,
           domain::Domain, state::State, sol::Solution)
```

Uses `renderer` to render a planning solution `sol` starting from a `state` in a PDDL `domain`. Constructs and returns a new [`Canvas`](@ref).
