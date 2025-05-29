`RandomSBM(bmap,pmat)` creates a random stochastic block model random graph. The vector `bmap` is a list of `n` positive integers giving the block number of vertices `1:n`. The `i,j`-entry of the matrix `pmat` gives the probability of an edge from a vertex in block `i` to a vertex in block `j`.

`RandomSBM(n,pvec,pmat)` creates such a graph with `n` vertices. The vector `pvec` gives the probabilities that vertices fall into a given block.
