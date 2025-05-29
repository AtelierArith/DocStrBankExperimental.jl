```
FilterQuery(query)
```

Simple property query; references agents via underscores `_`.

A query on an agent may result in an error; in that case, the agent will fail the filter condition by default.

See also [`@f_str`](@ref), [`filter`](@ref).

# Examples

```julia
filter(agents, f"_.age > 21 && _.name ∈ ['a', 'b']")
agents |> @filter _.age > 21 && _.name ∈ ['a', 'b']
```
