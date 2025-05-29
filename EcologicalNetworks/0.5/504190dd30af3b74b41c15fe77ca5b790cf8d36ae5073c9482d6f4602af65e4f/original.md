This abstract type groups all bipartite networks, regardless of the type of information. Bipartite networks have *two* fields for species, named `T` (for top, corresponding to matrix *rows*), and `B` (for bottom, matrix *columns*).

Any bipartite network can be declared (we'll use the example of a binary network) either using `BipartiteNetwork(A, T, B)` (assuming `A` is a matrix of interactions and `T` and `B` are vectors of species names for the top and bottom level), or `BipartiteNetwork(A)`, in which case the species will be named automatically.
