```julia
addnode!(model, component; label)

```

Adds a node to `model`. Component is `component` and `label` is `label` the label of node. Returns added node.

# Example

```jldoctest
julia> model = Model()
Model(numnodes:0, numedges:0, timesettings=(0.0, 0.01, 1.0))

julia> addnode!(model, SinewaveGenerator(), label=:gen)
Node(component:SinewaveGenerator(amp:1.0, freq:1.0, phase:0.0, offset:0.0, delay:0.0), idx:1, label:gen)
```
