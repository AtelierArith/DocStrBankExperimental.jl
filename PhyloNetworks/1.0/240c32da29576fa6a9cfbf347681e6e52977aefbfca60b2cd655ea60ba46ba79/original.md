```
pairwisetaxondistancematrix(net; keepInternal=false,
                            checkpreorder=true, nodeAges=[])
pairwisetaxondistancematrix!(M, net, nodeAges)
```

Return the matrix `M` of pairwise distances between nodes in the network:

  * between all nodes (internal and leaves) if `keepInternal=true`, in which case the nodes are listed in `M` in the order in which they appear in `net.vec_node`
  * between taxa only otherwise, in which case the nodes are listed in `M` in the order in which they appear in `tiplabels(net)` (i.e. same order as in `net.leaf`)

The second form modifies `M` in place, assuming all nodes.

The distance between the root and a given hybrid node (to take an example) is the weighted average of path lengths from the root to that node, where each path is weighted by the product of γs of all edges on that path. This distance measures the average genetic distance across the genome, if branch lengths are in substitutions/site.

optional arguments:

  * `checkpreorder`: if true, `net.vec_node` is updated to get a topological ordering of nodes.
  * `nodeAges`: if not provided, i.e. empty vector, the network is *not* modified.   If provided and non-empty, `nodeAges` should list node ages in the pre-order in which nodes are listed in `vec_node` (including leaves), and **edge lengths** in `net` **are modified** accordingly.

Providing node ages hence makes the network time consistent: such that all paths from the root to a given hybrid node have the same length. If node ages are not provided, the network need not be time consistent.
