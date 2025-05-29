```
 pschur(A::Vector{Matrix{T}}, E::Vector{Matrix{T}}; rev = true, withZ = true) -> (S, T, Q, Z, ev, ischur, α, γ)
```

Compute the extended periodic Schur decomposition of a square formal product of matrices  `inv(E(p))*A(p)*...*inv(E(2))*A(2)*inv(E(1))*A(1)`, if `rev = true` (default) or  `A(1)*inv(E(1))*A(2)*inv(E(2))*...*A(p)*inv(E(p))` if `rev = false`, without evaluating the product and the inverses.  The matrices `A(1)`, `...`, `A(p)` are contained in the `p`-vector of matrices `A`  such that the `i`-th matrix  `A(i)`, of dimensions `m(i)×n(i)`, is contained in `A[i]`. The square matrices `E(1)`, `...`, `E(p)` are contained in the `p`-vector of matrices `E`  such that the `i`-th matrix  `E(i)`, of dimensions `m(i)×m(i)` if `rev = true` or `n(i)×n(i)` if `rev = false`,  is contained in `E[i]`.

The resulting index `ischur` is determined such that `m(ischur) ≤ m(i), ∀i`. The resulting `p`-vectors `S`, `T`, `Q` and `Z` contain, respectively,  the matrices `S(1)`, `...`, `S(p)` with `S(ischur)` in a quasi-upper trapezoidal form and  `S(i)` upper trapezoidal for `i` $\neq$ `ischur`, the upper triangular matrices `T(1)`, `...`, `T(p)`,  the orthogonal matrices `Q(1)`, `...`, `Q(p)`, and `Z(1)`, `...`, `Z(p)`,  such that for `rev = true`

```
       Q(1)' * A(1) * Z(1) = S(1),  Q(1)' * E(1) * Z(2) = T(1), 
       Q(2)' * A(2) * Z(2) = S(2),  Q(2)' * E(2) * Z(3) = T(2),
              ...
       Q(p)' * A(p) * Z(p) = S(p),  Q(p)' * E(p) * Z(1) = T(p),
```

and for `rev = false`

```
       Q(1)' * A(1) * Z(1) = S(1),  Q(2)' * E(1) * Z(1) = T(1), 
       Q(2)' * A(2) * Z(2) = S(2),  Q(3)' * E(2) * Z(2) = T(2),
              ...
       Q(p)' * A(p) * Z(p) = S(p),  Q(1)' * E(p) * Z(p) = T(p),
```

The first `nmin` components of `ev := α .* γ` contain the *core eigenvalues* of the appropriate matrix product, where `nmin = m(ischur)`, while the last `nmax-nmin` components of `ev` are zero,  where `nmax` is the largest row or column dimension of `A(i)`, for `i = 1, ..., p`.  The eigenvalues can be alternatively expressed as `α .* γ`, where `γ` contains suitable  scaling parameters to avoid overflows or underflows in the expressions of the eigenvalues.  The performed orthogonal transformations are not accumulated if `withZ = false`,  in which case  `Q = nothing` and `Z = nothing`. 

The function `pschur` is based on wrappers for the SLICOT subroutines `MB03VW` (see [`PeriodicMatrices.SLICOTtools.mb03vw!`](@ref))  and `MB03BD` (see [`PeriodicMatrices.SLICOTtools.mb03bd!`](@ref)),  based on algorithms proposed in [1] and [2].

REFERENCES

[1] Bojanczyk, A., Golub, G. H. and Van Dooren, P.     The periodic Schur decomposition: algorithms and applications.     In F.T. Luk (editor), Advanced Signal Processing Algorithms,     Architectures, and Implementations III, Proc. SPIE Conference,     vol. 1770, pp. 31-42, 1992.

[2] Kressner, D.     An efficient and reliable implementation of the periodic QZ     algorithm. IFAC Workshop on Periodic Control Systems (PSYCO     2001), Como (Italy), August 27-28 2001. Periodic Control     Systems 2001 (IFAC Proceedings Volumes), Pergamon.
