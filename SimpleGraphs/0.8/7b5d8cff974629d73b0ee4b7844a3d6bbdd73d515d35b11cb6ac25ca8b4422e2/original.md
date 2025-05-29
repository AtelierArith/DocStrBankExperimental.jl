`incidence(G)` returns the vertex-edge incidence matrix of `G`.

Notes:

  * The result is a sparse matrix. Wrap in `Matrix` to convert to nonsparse.
  * Each column of the matrix has exactly one `+1` and one `-1`. If `G`

is undirected and an unsigned incidence matrix is desired, use `incidence(G,false)`.
