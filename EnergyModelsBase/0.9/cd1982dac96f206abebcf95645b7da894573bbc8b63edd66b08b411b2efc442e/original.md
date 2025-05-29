```
outputs(n::Node)
outputs(n::Node, p::Resource)
```

Returns the output resources of a node `n`, specified *via* the field `output`.

If the resource `p` is specified, it returns the value (1 in the case of [`Availability`](@ref), nothing in the case of a [`Sink`](@ref))
