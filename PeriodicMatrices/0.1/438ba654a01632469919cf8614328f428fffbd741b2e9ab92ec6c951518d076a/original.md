```
 pgschur(A::Array{Float64,3}, s::Union{Vector{Bool},BitVector}; rev = true, withQ = true) -> (S, Z, ev, ischur, α, γ)
```

Compute the generalized real periodic Schur decomposition of a formal product of square matrices  `A(p)^s(p)*...A(2)^s(2)*A(1)^s(1)`, if `rev = true` (default), or  `A(1)^s(1)*A(2)^s(2)*...*A(p)^s(p)`, if `rev = false`, where 's(j) = ±1'.  The matrices `A(1)`, `A(2)`, `...`, `A(p)` are contained in the `n×n×p` array `A`  such that the `i`-th matrix  `A(i)` is contained in `A[:,:,i]`. 

The resulting `n×n×p` array `S` contains the matrices `S(1)`, `...`, `S(p)`  such that `S(ischur)` is in a quasi-upper triangular form,  `S(i)` is upper triangular for `i` $\neq$ `ischur`.  If `withZ = true` (default), the resulting `n×n×p` array `Z` contains the orthogonal transformation  matrices `Z(1)`, `...`, `Z(p)`. The performed orthogonal transformations are not accumulated if `withZ = false`,  in which case `Z = nothing`. 

The resulting matrices satisfy for `rev = true`

```
       Z(mod(j,p)+1)' * A(j) * Z(j) = S(j),  if S[j] = true, 
       Z(j)' * A(j) * Z(mod(j,p)+1) = S(j),  if S[j] = false,
```

and for `rev = false`

```
       Z(j)' * A(j) * Z(mod(j,p)+1) = S(j),  if S[j] = true, 
       Z(mod(j,p)+1)' * A(j) * Z(j) = S(j),  if S[j] = false.
```

`S(i)` and `Z(i)` are contained in `S[:,:,i]` and `Z[:,:,i]`, respectively.  The vector `ev` contains the eigenvalues of the appropriate matrix product.  The eigenvalues can be alternatively expressed as `α .* γ`, where `γ` contains suitable  scaling parameters to avoid overflows or underflows in the expressions of the eigenvalues. 

The function `pgschur` is based on wrappers for the SLICOT subroutines `MB03VW`   (see [`PeriodicMatrices.SLICOTtools.mb03vw!`](@ref)) and `MB03BD`  (see [`PeriodicMatrices.SLICOTtools.mb03bd!`](@ref)),  based on algorithms proposed in [1] and [2].

REFERENCES

[1] Bojanczyk, A., Golub, G. H. and Van Dooren, P.     The periodic Schur decomposition: algorithms and applications.     In F.T. Luk (editor), Advanced Signal Processing Algorithms,     Architectures, and Implementations III, Proc. SPIE Conference,     vol. 1770, pp. 31-42, 1992.

[2] Kressner, D.     An efficient and reliable implementation of the periodic QZ     algorithm. IFAC Workshop on Periodic Control Systems (PSYCO     2001), Como (Italy), August 27-28 2001. Periodic Control     Systems 2001 (IFAC Proceedings Volumes), Pergamon.
