```
getdepth(idx, tree_type)
```

Get depth of `idx` in a binary tree or quadtree.

# Arguments

  * `idx::T where T<:Integer`: Index of a node.
  * `tree_type::Symbol`: Tree type. Supported types are `:binary` and `:quad` trees.

# Returns

`::T`: Depth of node `idx`.

# Examples

```@repl
using WaveletsExt

getdepth(1,:binary)     # 0
getdepth(3,:binary)     # 1
getdepth(8,:binary)     # 3

getdepth(1,:quad)       # 0
getdepth(3,:quad)       # 1
getdepth(8,:quad)       # 2
```

**See also:** [`Wavelets.Util.maketree`](@ref)
