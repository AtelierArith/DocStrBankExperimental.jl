```
objective(agent, max_t=Inf)
```

Return a function which takes a dictionary of agent parameters, and outputs a corresponding solution. Optionally specify simulation horizon `max_t`.

# Examples

```julia
o = objective(agent)
o(Dict("agent" => [1., 2.]))
```
