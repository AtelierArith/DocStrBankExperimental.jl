```
deleteleaf!(HybridNetwork, leafName::AbstractString; ...)
deleteleaf!(HybridNetwork, Node; ...)
deleteleaf!(HybridNetwork, Integer; index=false, ...)
```

Delete a node from the network, possibly from its name, number, or index in the network's array of nodes. The first two versions require that the node is a leaf. The third version does **not** require that the node is a leaf: If it has degree 3 or more, nothing happens. If it has degree 1 or 2, then it is deleted.

## keyword arguments

`simplify`: if true and if deleting the node results in 2 hybrid edges forming a cycle of k=2 nodes, then these hybrid edges are merged and simplified as a single tree edge.

`unroot`: if true, a root of degree 1 or 2 is deleted. If false, the root is deleted if it is of degree 1 (no root edge is left), but is kept if it is of degree 2. Deleting all leaves in an outgroup clade or grade will leave the ingroup rooted (that is, the new root will be of degree 2).

`nofuse`: if true, keep nodes (and edges) provided that they have at least one descendant leaf, even if they are of degree 2. This will keep two-cycles (forcing `simplify` to false). Nodes without any descendant leaves are deleted. If `nofuse` is false, edges adjacent to degree-2 nodes are fused.

`multgammas`: if true, the fused edge has γ equal to the product of the hybrid edges that have been fused together, which may result in tree edges with γ<1, or with reticulations in which the two parent γ don't add up to 1.

`keeporiginalroot`: if true, keep the root even if it is of degree one (forcing `unroot` to be false).

Warning: does **not** update edges' `containroot` nor internal attributes (e.g. those used by SNaQ for level-1 networks). Does not require branch lengths, and designed to work on networks of all levels.
