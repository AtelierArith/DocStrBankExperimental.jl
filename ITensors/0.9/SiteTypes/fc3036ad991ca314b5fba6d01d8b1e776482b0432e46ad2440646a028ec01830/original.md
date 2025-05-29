```
ops(s::Vector{<:Index}, os::Vector)
ops(os::Vector, s::Vector{<:Index})
```

Given a list of operators, create ITensors using the collection of indices.

# Examples

```julia
s = siteinds("Qubit", 4)
os = [("H", 1), ("X", 2), ("CX", 2, 4)]
# gates = ops(s, os)
gates = ops(os, s)
```
