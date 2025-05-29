```
displayedtrees(net::HybridNetwork, gamma::Float64; nofuse::Bool=false,
               unroot::Bool=false, multgammas::Bool=false,
               keeporiginalroot::Bool=false)
```

Extracts all trees displayed in a network, following hybrid edges with heritability >= γ threshold (or >0.5 if threshold=0.5) and ignoring any hybrid edge with heritability lower than γ. Returns an array of trees, as HybridNetwork objects.

`nofuse`: if true, do not fuse edges (keep degree-2 nodes) during hybrid edge removal.   `unroot`: if false, the root will not be deleted if it becomes of degree 2 unless   keeporiginalroot is true.   `multgammas`: if true, the edges in the displayed trees have γ values   equal to the proportion of genes that the edge represents, even though all   these edges are tree edges. The product of all the γ values across all edges   is the proportion of genes that the tree represents. More specifically,   edge `e` in a given displayed tree has γ equal to the product of γs   of all edges in the original network that have been merged into `e`.   `keeporiginalroot`: if true, keep root even if of degree 1.

Warnings:

  * if `nofuse` is true: the retained partner hybrid edges have their γ values unchanged, but their `ismajor` is changed to true
  * assume correct `ismajor` attributes.
