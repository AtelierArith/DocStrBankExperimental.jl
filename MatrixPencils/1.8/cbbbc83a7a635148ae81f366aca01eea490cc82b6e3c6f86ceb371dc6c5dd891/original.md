```
 pminv2ls(P; fast = true, contr = false, obs = false, minimal = false, atol = 0, rtol) -> (A, E, B, C, D)
```

Build a structured linearization as a system matrix `S(λ)` of the form

```
        | A-λE | B | 
 S(λ) = |------|---|
        |  C   | D |
```

of the inverse `R(λ) = inv(P(λ))`, such that `R(λ) = C*inv(λE-A)*B+D`.  The resulting linearization `S(λ)` preserves a part, if `minimal = false`, or  the complete Kronecker structure, if `minimal = true`, of `R(λ)`.  In the latter case, the order `n` of `A-λE` is the least possible one.

`P(λ)` can be specified as a polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`,  for which the coefficient matrices `P_i`, `i = 1, ..., k+1`, are stored in  the 3-dimensional matrix `P`, where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`). 

`P(λ)` can also be specified as a matrix or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

The computed structured linearization satisfies:

(1) `A-λE` is regular;

(2) `rank[B A-λE] = n` (controllability) if `minimal = true` or `contr = true`, in which case  the right Kronecker structure is preserved;

(3) `rank[A-λE; C] = n` (observability)  if `minimal = true` or `obs = true`, in which case  the left Kronecker structure is preserved;

(4) `S(λ)` has no simple infinite eigenvalues if `minimal = true`. 

If conditions (1)-(4) are satisfied, the linearization is called `minimal` and the resulting order `n` is the least achievable order. If conditions (1)-(3) are satisfied, the linearization is called `irreducible`  and the resulting order `n` is the least achievable order using orthogonal similarity transformations. For an irreducible linearization `S(λ)` preserves the pole-zero structure (finite and infinite) and the  left and right Kronecker structures of `R(λ)`. 

The keyword arguments `atol` and `rtol`, specify, respectively, the absolute and relative tolerance for the  nonzero coefficients of the matrix `P(λ)`. The default relative tolerance is `nt*ϵ`,  where `nt` is the size of the square matrix `P(λ)` and `ϵ` is the machine epsilon of the element type of its coefficients. 

The structured linearization is built using the methods described in [1].

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).
