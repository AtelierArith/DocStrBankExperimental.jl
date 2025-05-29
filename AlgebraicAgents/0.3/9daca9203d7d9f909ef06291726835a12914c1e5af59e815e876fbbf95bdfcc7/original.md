```
simulate(agent::AbstractAlgebraicAgent, max_t=Inf)::AbstractAlgebraicAgent
```

Solves an (initialized) problem.  Runs a loop until all the agents return `true` (reached simulation horizon) or `nothing` (delegated evolution), or until the simulation horizon reaches `max_t`. Avoids front-running.

# Examples

```julia
sol = simulate(model)
```
