```
inputs(n::Node)
inputs(n::Node, p::Resource)
```

Returns the input resources of a node `n`, specified *via* the field `input`.

If the resource `p` is specified, it returns the value (1 in the case of [`Availability`](@ref), nothing in the case of a [`Source`](@ref))
