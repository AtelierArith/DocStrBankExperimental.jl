```
minortreeat(net::HybridNetwork, hybindex::Integer, nofuse=false, unroot::Bool=false)
```

Extract the tree displayed in the network, following the major hybrid edge at each hybrid node, except at the ith hybrid node (i=`hybindex`), where the minor hybrid edge is kept instead of the major hybrid edge. If `nofuse` is true, edges are not fused (degree-2 nodes are kept). If `unroot` is true, the root will be deleted if it becomes of degree 2.

Warning: assume correct `ismajor` fields.
