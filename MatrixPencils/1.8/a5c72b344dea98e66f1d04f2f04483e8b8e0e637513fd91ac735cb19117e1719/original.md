```
 lpmfd2ls(DEN, NUM; fast = true, contr = false, obs = false, minimal = false, atol = 0, rtol) -> (A, E, B, C, D)
```

Build a structured linearization as a system matrix `S(λ)` of the form

```
        | A-λE | B | 
 S(λ) = |------|---|
        |  C   | D |
```

of the left polynomial matrix fractional description `R(λ) = inv(DEN(λ))*NUM(λ)`,  such that `R(λ) = C*inv(λE-A)*B+D`. The resulting linearization `S(λ)` preserves a part,  if `minimal = false`, or the complete Kronecker structure, if `minimal = true`, of `R(λ)`.  In the latter case, the order `n` of `A-λE` is the least possible one.

`DEN(λ)` and `NUM(λ)` can be specified as polynomial matrices of the form `X(λ) = X_1 + λ X_2 + ... + λ**k X_(k+1)`,  for `X = DEN` or `X = NUM`, for which the coefficient matrices `X_i`, `i = 1, ..., k+1`, are stored in  the 3-dimensional matrices `X`, where `X[:,:,i]` contains the `i`-th coefficient matrix `X_i` (multiplying `λ**(i-1)`). 

`DEN(λ)` and `NUM(λ)` can also be specified as matrices, vectors or scalars of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.    In this case, no check is performed that `N(λ)` and `D(λ)` have the same indeterminates.

The computed structured linearization satisfies:

(1) `A-λE` is regular;

(2) `rank[B A-λE] = n` (controllability) if `minimal = true` or `contr = true`, in which case  the right Kronecker structure is preserved;

(3) `rank[A-λE; C] = n` (observability)  if `minimal = true` or `obs = true`, in which case  the left Kronecker structure is preserved;

(4) `S(λ)` has no simple infinite eigenvalues if `minimal = true`. 

If conditions (1)-(4) are satisfied, the linearization is called `minimal` and the resulting order `n` is the least achievable order. If conditions (1)-(3) are satisfied, the linearization is called `irreducible`  and the resulting order `n` is the least achievable order using orthogonal similarity transformations. For an irreducible linearization `S(λ)` preserves the pole-zero structure (finite and infinite) and the  left and right Kronecker structures of `R(λ)`. 

The keyword arguments `atol` and `rtol`, specify, respectively, the absolute and relative tolerance for the  nonzero coefficients of the matrices `DEN(λ)` and `NUM(λ)`. The default relative tolerance is `nt*ϵ`,  where `nt` is the size of the square matrix `DEN(λ)` and `ϵ` is the machine epsilon of the element type of its coefficients. 

The structured linearization is built using the methods described in [1].

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).
