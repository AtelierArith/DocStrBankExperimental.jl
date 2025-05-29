```
function leave_incidence_matrix(root::G)::Matrix{Float64} where {G<:AbstractNode}
```

Calculate the incidence matrix of the tree whos root node is `root` For a tree with $m$ leaves and $n$ vertecies this function returns an $m \times n$ matrix $L$, where $L_{ij} = 1$ if vertex $j$ is on the path from leave $i$ to the root of the tree and $0$ otherwise.

Returns leave incidence matrix.

  * `root` : Root node of the tree
