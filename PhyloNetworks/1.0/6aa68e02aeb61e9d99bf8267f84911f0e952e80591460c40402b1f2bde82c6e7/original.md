```
directedges!(net::HybridNetwork; checkMajor::Bool=true)
```

Updates the edges' attribute `ischild1`, according to the root placement. Also updates edges' attribute `containroot`, for other possible root placements compatible with the direction of existing hybrid edges. Relies on hybrid nodes having exactly 1 major hybrid parent edge, but checks for that if `checkMajor` is true.

Warnings:

1. Assumes that `ischild1` is correct on hybrid edges (to avoid changing the identity of which nodes are hybrids and which are not).
2. Does not check for cycles (to maintain a network's DAG status)

Returns the network. Throws a 'RootMismatch' Exception if the root was found to conflict with the direction of any hybrid edge.
