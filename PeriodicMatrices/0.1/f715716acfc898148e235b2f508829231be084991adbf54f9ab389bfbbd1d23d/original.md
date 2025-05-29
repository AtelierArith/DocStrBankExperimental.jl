```
 psordschur!(S::Vector{Matrix{Float64}}, Z::Vector{Matrix{Float64}}, select; rev, schurindex)
```

Reorder the core eigenvalues of the product `Π = S[p]*...*S[2]*S[1]`, if `rev = true` (default) or `Π = S[1]*S[2]*...*S[p]` if `rev = false`, where `Π` is in real Schur form, such that the selected eigenvalues in the logical array `select` are moved into the leading positions.  The `p`-vectors `S` and `Z` contain the matrices `S[1]`, `...`, `S[p]` in an extended periodic Schur form, with the leading square block of  `S[schurindex]` in real Schur form, and the corresponding orthogonal transformation matrices `Z[1]`, `...`, `Z[p]`, respectively.  `S` and `Z` are overwritten by the updated matrices.  A conjugate pair of eigenvalues must be either both included or both excluded via `select`.  The dimension of select must be equal to the number of core eigenvalues (i.e., the minimum dimension of matrices in the vector `S`).  
