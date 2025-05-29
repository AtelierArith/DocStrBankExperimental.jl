```
replicate!(agent::AbstractAgent model; kwargs...)
```

Add a new agent to the `model` copying the values of the fields of the given agent. With the `kwargs` it is possible to override the values by specifying new ones for some fields, including the `pos` field. The `id` field is set to a new one automatically.

Return the new agent instance.

## Example

```julia
using Agents
@agent struct A(GridAgent{2})
    k::Float64
    w::Float64
end

model = StandardABM(A, GridSpace((5, 5)))
a = A(1, (2, 2), 0.5, 0.5)
b = replicate!(a, model; w = 0.8)
```
