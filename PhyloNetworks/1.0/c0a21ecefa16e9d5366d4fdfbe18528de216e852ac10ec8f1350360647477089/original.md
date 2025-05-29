```
biconnectedcomponents(network, ignoreTrivial=false)
```

Calculate biconnected components (aka "blobs") using Tarjan's algorithm.

Output: array of arrays of edges.

  * the length of the array is the number of blobs
  * each element is an array of all the edges inside a given blob.

These blobs are returned in post-order, but within a blob, edges are *not* necessarily sorted in topological order. If `ignoreTrivial` is true, trivial components (of a single edge) are not returned. The network is assumed to be connected.

*Warnings*: for nodes, fields `intn2` and `intn1` are modified during the algorithm. They are used to store the node's "index" (time of visitation), "lowpoint", and the node's "parent", as defined by the order in which nodes are visited. For edges, field `boole2` is modified, to store whether the edge has been already been visited or not.

References:

  * p. 153 of [Tarjan (1972)](http://epubs.siam.org/doi/pdf/10.1137/0201010). Depth first search and linear graph algorithms, SIAM Journal on Computing, 1(2):146-160
  * on [geeksforgeeks](https://www.geeksforgeeks.org/biconnected-components/), there is an error (as of 2018-01-30): `elif v != parent[u] and low[u] > disc[v]:` (python version) should be replaced by `elif v != parent[u] and disc[u] > disc[v]:`
  * nice explanation at this [url](https://www.cs.cmu.edu/~avrim/451f12/lectures/biconnected.pdf)
