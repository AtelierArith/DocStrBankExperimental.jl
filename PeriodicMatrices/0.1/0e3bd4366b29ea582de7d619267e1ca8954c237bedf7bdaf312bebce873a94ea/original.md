```
 pschur(A::Vector{Matrix{T}}; rev = true, withZ = true) -> (S, Z, ev, ischur, α, γ)
 pschur1(A::Vector{Matrix{T}}; rev = true, withZ = true) -> (S, Z, ev, ischur, α, γ)
```

Compute the extended periodic Schur decomposition of a square product of matrices  `A(p)*...*A(2)*A(1)`, if `rev = true` (default) or `A(1)*A(2)*...*A(p)` if `rev = false`, without evaluating the product.  The matrices `A(1)`, `...`, `A(p)` are contained in the `p`-vector of matrices `A`  such that the `i`-th matrix  `A(i)`, of dimensions `m(i)×n(i)`, is contained in `A[i]`. The resulting `p`-vectors `S` and `Z` contain the matrices `S(1)`, `...`, `S(p)` and the orthogonal matrices `Z(1)`, `...`, `Z(p)`, respectively,  such that for `rev = true`

```
       Z(2)' * A(1) * Z(1) = S(1),
       Z(3)' * A(2) * Z(2) = S(2),
              ...
       Z(1)' * A(p) * Z(p) = S(p),
```

and for `rev = false`

```
       Z(1)' * A(1) * Z(2) = S(1),
       Z(2)' * A(2) * Z(3) = S(2),
              ...
       Z(p)' * A(p) * Z(1) = S(p).
```

The resulting index `ischur` is determined such that `m(ischur) ≤ m(i), ∀i`. The resulting `S(i)`, for `i = 1, ..., p` are in an extended  periodic Schur form,  with `S(ischur)` in a quasi-upper trapezoidal form and `S(i)`  upper trapezoidal for `i` $\neq$ `ischur`.  `S(i)` and `Z(i)` are contained in `S[i]` and `Z[i]`, respectively.  The first `nmin` components of `ev := α .* γ` contain the *core eigenvalues* of the appropriate matrix product, where `nmin = m(ischur)`, while the last `nmax-nmin` components of `ev` are zero,  where `nmax` is the largest row or column dimension of `A(i)`, for `i = 1, ..., p`.  The eigenvalues can be alternatively expressed as `α .* γ`, where `γ` contains suitable  scaling parameters to avoid overflows or underflows in the expressions of the eigenvalues.  The performed orthogonal transformations are not accumulated if `withZ = false`,  in which case `Z = nothing`. 

The function `pschur` is based on wrappers for the SLICOT subroutines `MB03VW` (see [`PeriodicMatrices.SLICOTtools.mb03vw!`](@ref))  and `MB03BD` (see [`PeriodicMatrices.SLICOTtools.mb03bd!`](@ref)),  based on algorithms proposed in [1] and [2].

The function `pschur1` is based on wrappers for the SLICOT subroutines `MB03VD` (see [`PeriodicMatrices.SLICOTtools.mb03vd!`](@ref)),  `MB03VY` (see [`PeriodicMatrices.SLICOTtools.mb03vy!`](@ref)),  and `MB03BD` (see [`PeriodicMatrices.SLICOTtools.mb03bd!`](@ref)),  based on algorithms proposed in [1] and [2].

REFERENCES

[1] Bojanczyk, A., Golub, G. H. and Van Dooren, P.     The periodic Schur decomposition: algorithms and applications.     In F.T. Luk (editor), Advanced Signal Processing Algorithms,     Architectures, and Implementations III, Proc. SPIE Conference,     vol. 1770, pp. 31-42, 1992.

[2] Kressner, D.     An efficient and reliable implementation of the periodic QZ     algorithm. IFAC Workshop on Periodic Control Systems (PSYCO     2001), Como (Italy), August 27-28 2001. Periodic Control     Systems 2001 (IFAC Proceedings Volumes), Pergamon.
