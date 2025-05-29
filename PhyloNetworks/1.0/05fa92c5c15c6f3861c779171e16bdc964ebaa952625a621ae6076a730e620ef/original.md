```
isgalled(net::HybridNetwork, checkpreorder::Bool=true)
```

`true` (resp. `false`) if `net` is (resp. is not) a galled network, assuming that `net` is bicombining (every hybrid has exactly 2 parents). A network is galled if every hybrid node is contained in a cycle that has its 2 hybrid parent edges and otherwise tree edges only. See for example [Huson, Rupp & Scornavacca (2010)](https://doi.org/10.1017/CBO9780511974076) and [Gunawan, DasGupta & Zhang (2017)](https://doi.org/10.1016/j.ic.2016.11.001). Equivalently, a bicombining network is galled if, for any hybrid node `n`, both of its parent edges originate from the same tree component. We get the tree components by deleting all hybrid edges from the network: we are left with a forest of trees.

The network is traversed in preorder (from the root to the leaves). Turn `checkpreorder` to `false` if the pre-ordering was run and is known to be up-to-date. Assumption: tree edges are directly correctly according to the current root.
