```
deletehybridthreshold!(net::HybridNetwork, threshold::Float64,
                       nofuse=false, unroot=false, multgammas=false,
                       keeporiginalroot=false)
```

Deletes from a network all hybrid edges with heritability below a threshold gamma. Returns the network.

  * if threshold<0.5: delete minor hybrid edges with γ < threshold (or with a missing γ, for any threshold > -1.0)
  * if threshold=0.5: delete all minor hybrid edges (i.e normally with γ < 0.5, if γ non-missing)
  * `nofuse`: if true, do not fuse edges and keep original nodes.
  * `unroot`: if false, the root will not be deleted if it becomes of degree 2.
  * `multgammas`: if true, the modified edges have γ values equal to the proportion of genes that the extracted subnetwork represents. For an edge `e` in the modified network, the inheritance γ for `e` is the product of γs of all edges in the original network that have been merged into `e`.

-`keeporiginalroot`: if true, the root will be retained even if of degree 1.

Warnings:

  * by default, `nofuse` is false, partner hybrid edges are fused with their child edge and have their γ changed to 1.0. If `nofuse` is true: the γ's of partner hybrid edges are unchanged.
  * assumes correct `ismajor` fields, and correct `ischild1` fields to update `containroot`.
