This abstract type groups all unipartite networks, regardless of the type of information. Unipartite networks have *a single* field for species, named `S`, which has the same number of elements as the size of the matrix.

Any unipartite network can be declared (we'll use the example of a binary network) either using `UnipartiteNetwork(A, S)` (assuming `A` is a matrix of interactions and `S` is a vector of species names), or `UnipartiteNetwork(A)`, in which case the species will be named automatically.
