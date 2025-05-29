```
render_sol!(canvas::Canvas, renderer::Renderer,
            domain::Domain, state::State, sol::Solution)
```

Uses `renderer` to render a planning solution `sol` starting from a `state` in a PDDL `domain`. Renders to a `canvas` on top of any existing content.
