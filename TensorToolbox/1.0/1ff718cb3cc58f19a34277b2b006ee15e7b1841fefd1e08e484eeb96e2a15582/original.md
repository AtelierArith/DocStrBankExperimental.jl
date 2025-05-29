```
dimtree(leaves::AbstractVector{<:Integer}[,internal_nodes::AbstractVector{<:Integer}])
dimtree(N[,treetype])
```

Dimension tree. Create from:

  * a vector of leaves (and a vector of internal nodes),
  * an order of a tensor N and a type treetype of a dimtree. Default: treetype="balanced".
