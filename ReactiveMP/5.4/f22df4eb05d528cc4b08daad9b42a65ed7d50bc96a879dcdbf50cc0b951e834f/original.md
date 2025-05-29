`PermutationMatrix(ind::Array{T})` creates a permutation matrix with ones at coordinates `(k, ind[k]) for k = 1:length(ind)`.

A permutation matrix represents a matrix containing only zeros and ones, which basically permutes the vector or matrix it is multiplied with. These matrices A are constrained by:

$$
    A_{ij} = \{0, 1\}\\
    ∑_{i} A_{ij} = 1\\
    ∑_{j} A_{ij} = 1
$$

An example is the 3-dimensional permutation matrix

$$
A = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 0 & 1 \\ 1 & 0 & 0 \end{bmatrix}
$$
