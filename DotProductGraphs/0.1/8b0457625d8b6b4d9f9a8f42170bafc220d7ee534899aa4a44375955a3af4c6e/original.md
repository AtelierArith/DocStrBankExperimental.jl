`dot_product(L,R;to_prob = true)`

Computes the dot product between two embeddings and gives back a matrix of interaction probabilities

The left and right embeddings must be of the same dimension (e.g., `size(L)[2] == size(R)[2]`) but can be of different number of nodes (e.g. for bipartite networks).

# Arguments

  * `L`: Left embedding
  * `R`: Right embedding
  * `to_prob`: (optional) whether to clamp the outcomes to the interval [0,1]

# Examples

```julia
julia> # we first build a 2 blocks matrix:
julia> block_matrix = reshape([ones(5,5) zeros(5,5); zeros(5,5) ones(5,5)],10,10)
julia> # and then decompose it:
julia> L,R = svd_embedding(block_matrix,2) # or, automatically L,R = svd_embedding(block_matrix)
julia> dot_product(L,R) ≈ block_matrix
```
