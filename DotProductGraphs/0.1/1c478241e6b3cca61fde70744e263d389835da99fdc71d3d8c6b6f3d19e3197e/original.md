`svd_embedding(A,svd_engine,d)`

Computes an SVD embedding of an adjacency matrix `A` of dimension `d`, using `svd_engine` to perform the SVD factorization

Given an adjacency matrix A, the function returns its node embedding using the Singular Value Decomposition, as it is done in Random Dot Product Graphs. The functions accepts a user defined `svd_engine` that can be different from the detaul `svd()` coming from `LinearAlgebra`. In that case, `svd_engine` must be a function of the same form of `truncated_svd`.

# Arguments

  * `A`: Adjacency matrix of the graph to embed.
  * `d`: If an `Int`, the dimension of the embedding. If it is left to nothing, the function uses Zhu&Ghodsi method to estimate the optimal embedding dimension. Or it can be a user defined function that returns the optimal dimension of the embedding.
  * `svd_engine`: The function used to perform the SVD factorization, by default `svd()` from `LinearAlgebra`

# Notes

  * The matrix `A` can be asymmetric (that is, the graph can be directed) and rectangular (e.g., for bipartite graphs).

# Examples

```julia
julia> # we first build a 2 blocks matrix:
julia> block_matrix = reshape([ones(5,5) zeros(5,5); zeros(5,5) ones(5,5)],10,10)
julia> # and then decompose it by specifying a dimensionality
julia> L,R = svd_embedding(block_matrix,4)
julia> # or automatically
julia> L,R = svd_embedding(block_matrix)

```
