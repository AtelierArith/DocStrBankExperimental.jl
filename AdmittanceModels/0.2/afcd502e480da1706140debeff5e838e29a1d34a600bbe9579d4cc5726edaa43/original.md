```
PSOModel(circuit::Circuit, port_edges::Vector{<:Tuple},
    port_names::AbstractVector)
```

Create a PSOModel for a circuit with ports on given edges. The spanning tree where the first vertex is chosen as ground and all other vertices are neighbors of ground is used.
