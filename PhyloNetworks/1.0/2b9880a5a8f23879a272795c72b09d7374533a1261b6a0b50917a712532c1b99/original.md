```
istreechild(net::HybridNetwork)
```

Tuple `(rooted, semi_weakly, semi_strongly)` in which each element is true or false, to indicate if `net` is / is not

  * tree-child as a rooted network
  * weakly tree-child as a semidirected network
  * strongly tree-child as a semidirected network

A rooted network is tree-child if all of its internal nodes have at least one child that is a tree node (or equivalently, one child edge that is a tree edge). A semidirected network is strongly (resp. weakly) tree-child if all (resp. at least one) of its rooted partners are tree-child.

Note that degree-2 nodes are not suppressed: a degree-2 node with a single hybrid child causes the network to *not* be tree-child, despite the fact that suppressing this node may render the reduced network tree-child.

Assumes that tree edges are directly correctly according to the current root.
