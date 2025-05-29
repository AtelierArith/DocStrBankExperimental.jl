```
majortree(net::HybridNetwork; nofuse::Bool=false, unroot::Bool=false,
          keeporiginalroot::Bool=false)
```

Extract the major tree displayed in a network, keeping the major edge and dropping the minor edge at each hybrid node.

`nofuse`: if true, edges and degree-2 nodes are retained during edge removal. Otherwise, at each reticulation the child edge (below the hybrid node) is retained: the major hybrid edge is fused with it.

`unroot`: is true, the root will be deleted if it becomes of degree 2.

`keeporiginalroot`: the network's root is kept even if it becomes of degree 1.

Warnings:

  * if `nofuse` is true: the hybrid edges that are retained (without fusing) have their γ values unchanged, but their `ismajor` is changed to true
  * assume correct `ismajor` attributes.
