DenseNautyDiGraph(size::Int)
  DenseNautyDiGraph(adj::Matrix)
  DenseNautyDiGraph(g::AbstractGraph)

Constructs a new dense Nauty directed graph.

A dense Nauty directed graph is a bit matrix: if the graph has `n` vertices, then it is coded as an `(WORDSIZE*m)×n` bit matrix, with `m=(n+WORDSIZE-1)÷WORDSIZE`. Each column of that matrix is thus a chunk of memory of size `m`, and the `i`th column represents the adjacency list of the the `i`th vertex. The bits are reversed in each word, so to know if the `i`th vertex is connected to vertex `j`, check the field `data[setpos(j),i]`.
