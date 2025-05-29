```
HybridNetwork
```

Subtype of abstract `Network` type. Explicit network or tree with the following attributes:

  * `numtaxa`: number of taxa, that is, number of are leaves (or tips). Leaves are required to be attached to a single edge.
  * `numnodes`: total number of nodes: tips and internal nodes
  * `numedges`: total number of edges
  * `numhybrids`: total number of hybrid nodes
  * `edge`: vector of Edges
  * `node`: vector of Nodes
  * `rooti`: index of the root in vector 'node'. May be artificial in a semidirected network, but is necessary for printing and traversal purposes.
  * `hybrid`: vector of Nodes: those are are hybrid nodes
  * `leaf`: vector of Nodes: those that are leaves
  * `fscore`: score after fitting network to data, i.e. parsimony score, or multipe of the negative log pseudodeviance for SNaQ
  * `isrooted`: true or false
  * `partition`: vector of `Partition`
