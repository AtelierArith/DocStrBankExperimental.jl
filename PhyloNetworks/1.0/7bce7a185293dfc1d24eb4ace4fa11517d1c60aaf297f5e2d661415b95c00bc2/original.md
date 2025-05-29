```
displayednetworkat!(net::HybridNetwork, node::Node, nofuse=false,
                    unroot=false, multgammas=false)
```

Delete all the minor hybrid edges, except at input node. The network is left with a single hybridization, and otherwise displays the same major tree as before. If `nofuse` is true, edges are not fused (degree-2 nodes are kept).

Warning: assume correct `ismajor` fields.
