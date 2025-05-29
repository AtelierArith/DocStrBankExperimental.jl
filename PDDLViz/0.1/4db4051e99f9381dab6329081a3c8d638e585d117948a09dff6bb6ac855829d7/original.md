```
Renderer
```

A `Renderer` defines how a PDDL [`State`](@ref) for a specific [`Domain`](@ref) should be rendered. A concrete sub-type of `Renderer` should be implemented for a PDDL domain (or family of PDDL domains, e.g. 2D gridworlds) for users who wish to visualize that domain.

```
(r::Renderer)(domain::Domain, args...; options...)
(r::Renderer)(canvas::Canvas, domain::Domain, args...; options...)
```

Once a `Renderer` has been constructed, it can be used to render PDDL states and other entities by calling it with the appropriate arguments.
