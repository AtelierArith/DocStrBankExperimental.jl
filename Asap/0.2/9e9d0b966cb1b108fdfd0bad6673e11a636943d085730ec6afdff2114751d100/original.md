```
planarize!(nodes, plane = :XY)
```

Restrict the DOFs of a set of nodes to a given global plane. E.g., when analyzing a 2D structure.

# Arguments

  * `nodes::Vector{<:AbstractNode}` vector of nodes to restrict
  * `plane::Symbol = :XY` plane to restrict DOFs. Defaults to the XY plane, can be:

      * :XY
      * :XZ
      * :YZ
