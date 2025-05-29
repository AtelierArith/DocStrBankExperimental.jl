```
 pgordschur!(S::Array{Float64,3}, s::Union{Vector{Bool},BitVector}, Z::Array{Float64,3}, select::Union{Vector{Bool},BitVector}; rev, schurindex)
```

Reorder the eigenvalues of the product `Π = S[:,:,p]^s[p]*...*S[:,:,2]^s[2]*S[:,:,1]^s[1]`, if `rev = true` (default) or  `Π = S[:,:,1]^s[1]*S[:,:,2]^s[2]*...*S[:,:,p]^s[p]` if `rev = false`, with 's[j] = ±1', where `Π` is in a real Schur form,  such that the selected eigenvalues in the logical array `select` are moved into the leading positions.  The 3-dimensional arrays `S` and `Z` contain the matrices `S[:,:,1]`, `...`, `S[:,:,p]` in a generalized periodic Schur form,  with `S[:,:,schurindex]` in a quasi-upper triangular (real Schur) form,  and the corresponding orthogonal transformation matrices `Z[:,:,1]`, `...`, `Z[:,:,p]`, respectively.   `S` and `Z` are overwritten by the updated matrices.  A conjugate pair of eigenvalues must be either both included or both excluded via `select`.    
