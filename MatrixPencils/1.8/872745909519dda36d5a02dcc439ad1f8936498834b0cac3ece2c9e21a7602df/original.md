```
 spm2ls(T, U, V, W; fast = true, contr = false, obs = false, minimal = false, atol = 0, rtol) -> (A, E, B, C, D)
```

Build a structured linearization as a system matrix `S(λ)` of the form

```
        | A-λE | B | 
 S(λ) = |------|---|
        |  C   | D |
```

of the structured polynomial matrix 

```
          | -T(λ) | U(λ) |
   P(λ) = |-------|------|
          | V(λ)  | W(λ) |
```

such that `V(λ)*inv(T(λ))*U(λ)+W(λ) = C*inv(λE-A)*B+D`. The resulting linearization `S(λ)` preserves a part,  if `minimal = false`, or the complete Kronecker structure, if `minimal = true`, of `P(λ)`. In the latter case,  the order `n` of `A-λE` is the least possible one and `S(λ)` is a strong linearization of `P(λ)`.

`T(λ)`, `U(λ)`, `V(λ)`, and `W(λ)` can be specified as polynomial matrices of the form `X(λ) = X_1 + λ X_2 + ... + λ**k X_(k+1)`,  for `X = T`, `U`, `V`, and `W`, for which the coefficient matrices `X_i`, `i = 1, ..., k+1`, are stored in  the 3-dimensional matrices `X`, where `X[:,:,i]` contains the `i`-th coefficient matrix `X_i` (multiplying `λ**(i-1)`). 

`T(λ)`, `U(λ)`, `V(λ)`, and `W(λ)` can also be specified as matrices, vectors or scalars of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

The computed structured linearization satisfies:

(1) `A-λE` is regular;

(2) `rank[B A-λE] = n` (controllability) if `minimal = true` or `contr = true`, in which case  the finite and right Kronecker structures are preserved;

(3) `rank[A-λE; C] = n` (observability)  if `minimal = true` or `obs = true`, in which case  the finite and left Kronecker structures are preserved;

(4) `A-λE` has no simple infinite eigenvalues if `minimal = true`, in which case the complete Kronecker structure is preserved. 

The keyword arguments `atol` and `rtol`, specify, respectively, the absolute and relative tolerance for the  nonzero coefficients of the matrices `T(λ)`, `U(λ)`, `V(λ)` and `W(λ)`. The default relative tolerance is `nt*ϵ`,  where `nt` is the size of the square matrix `T(λ)` and `ϵ` is the machine epsilon of the element type of its coefficients. 

The structured linearization is built using the methods described in [1].

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).
