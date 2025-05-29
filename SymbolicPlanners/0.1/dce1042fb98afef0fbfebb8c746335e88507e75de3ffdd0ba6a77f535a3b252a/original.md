```julia
abstract type Planner
```

Abstract planner type. Once constructed, a `planner` can be run on a `domain`, initial `state`, and a `spec`, returning a [`Solution`](@ref). A `problem` can be provided instead of a `state` and `spec`:

```
planner(domain::Domain, state::State, spec)
planner(domain::Domain, problem::Problem)
```

New planners should define [`solve`](@ref) and (optionally) [`refine!`](@ref).
