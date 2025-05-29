```
LayerMap(index, rule)
```

Composite primitive that maps an LRP-rule to all layers in the model at the given index. The index can either be an integer or a tuple of integers to map a rule to a specific layer in nested Flux `Chain`s.

See [`show_layer_indices`](@ref) to print layer indices and [`Composite`](@ref) for an example.
