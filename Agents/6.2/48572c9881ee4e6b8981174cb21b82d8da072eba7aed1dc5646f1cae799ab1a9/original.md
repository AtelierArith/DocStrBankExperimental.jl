```
add_agent!([pos,] model::ABM, args...) → newagent
add_agent!([pos,] model::ABM; kwargs...) → newagent
```

Use one of these two versions to create and add a new agent to the model using the constructor of the agent type of the model. Optionally provide a position to add the agent to as *first argument*, which must match the space position type.

This function takes care of setting the agent id *and* position. The extra provided `args...` or `kwargs...` are propagated to other fields of the agent constructor (see example below). Mixing `args...` and `kwargs...` is not possible, only one of the two can be used to set the fields.

```
add_agent!([pos,] A::Type, model::ABM, args...) → newagent
add_agent!([pos,] A::Type, model::ABM; kwargs...) → newagent
```

Use one of these two versions for mixed agent models, with `A` the agent type you wish to create, because it is otherwise not possible to deduce a constructor for `A`.

## Example

```julia
using Agents
@agent struct Agent(GraphAgent)
    w::Float64 = 0.1
    k::Bool = false
end
model = StandardABM(Agent, GraphSpace(complete_digraph(5)))

add_agent!(model, 1, 0.5, true) # incorrect: id/pos is set internally
add_agent!(model, 0.5, true) # correct: w becomes 0.5
add_agent!(5, model, 0.5, true) # add at position 5, w becomes 0.5
add_agent!(model; w = 0.5) # use keywords: w becomes 0.5, k becomes false
```
