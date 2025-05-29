```
transform(agent::AbstractAlgebraicAgent, queries...)
tranform(agent::Vector{<:AbstractAlgebraicAgent}, queries...)
```

Run transform query on agents in a hierarchy.

A query on an agent may result in an error; in that case, the respective agent's output is omitted for the result.

See also [`@transform`](@ref).

# Examples

```julia
agent |> @transform(name=_.name)
agent |> @transform(name=_.name, _.age)
```
