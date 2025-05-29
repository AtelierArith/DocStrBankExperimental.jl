```
walk!(agent, direction::NTuple, model::ABM{<:AbstractGridSpace}; ifempty = true)
walk!(agent, direction::SVector, model::ABM{<:ContinuousSpace})
```

Move agent in the given `direction` respecting periodic boundary conditions. For non-periodic spaces, agents will walk to, but not exceed the boundary value. Available for both `AbstractGridSpace` and `ContinuousSpace`s.

The type of `direction` must be the same as the space position. `AbstractGridSpace` asks for `Int` tuples, and `ContinuousSpace` for `Float64` static vectors, describing the walk distance in each direction. `direction = (2, -3)` is an example of a valid direction on a `AbstractGridSpace`, which moves the agent to the right 2 positions and down 3 positions. Agent velocity is ignored for this operation in `ContinuousSpace`.

## Keywords

  * `ifempty` will check that the target position is unoccupied and only move if that's true. Available only on `AbstractGridSpace`.

Example usage in [Battle Royale](     https://juliadynamics.github.io/AgentsExampleZoo.jl/dev/examples/battle/).
