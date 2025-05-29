```
FDMnode(x::Real, y::Real, z::Real, dof::Bool, id = :node)
FDMnode(pos::Vector{<:Real}, dof::Bool, id = :node)
```

A node in an FDM network defined by its spatial position [x, y, z] and degree of freedom (free = `true`, fixed = `false`)

# Fields

  * position::Vector{Float64}: the [x,y,z] position of the node
  * dof::Bool: true = free; false = fixed
  * id::Symbol: identifier (optional)
  * nodeID::Integer: global indentifier (internal)
  * reaction::Vector{Float64}: the [x,y,z] reaction forces if node is fixed
