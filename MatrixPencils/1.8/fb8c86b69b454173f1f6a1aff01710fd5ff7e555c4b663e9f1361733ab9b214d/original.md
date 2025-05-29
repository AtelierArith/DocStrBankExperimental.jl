```
 pm2lps(P; contr = false, obs = false) -> (A, E, B, F, C, G, D, H)
```

Build a structured linearization as a system matrix `S(λ)` of the form

```
        | A-λE | B-λF | 
 S(λ) = |------|------|
        | C-λG | D-λH |
```

of the polynomial matrix `P(λ)` which preserves a part of the Kronecker structure of `P(λ)`. 

`P(λ)` can be specified as a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`,  for which the coefficient matrices `P_i`, `i = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`). 

`P(λ)` can also be specified as a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

If `d` is the degree of the `p x m` polynomial matrix `P(λ)`, then the computed linearization satisfies:

(1) `A-λE` is a `n x n` regular pencil, where `n = p(d-1)` if `contr = false` and `p <= m` and `n = m(d-1)` otherwise; 

(2) `P(λ) = (C-λG)*inv(λE-A)*(B-λF)+D-λH`;

(3) `rank[B-λF A-λE] = n` for any finite and infinite `λ` (strong controllability) if `contr = true`, in which case  the right Kronecker structure is preserved;

(4) `rank[A-λE; C-λG] = n` for any finite and infinite `λ` (strong observability)  if `obs = true`, in which case  the left Kronecker structure is preserved. 

If conditions (1)-(4) are satisfied, the linearization is called `strongly minimal`, the resulting order `n` is the least achievable order and `S(λ)` preserves the pole-zero structure (finite and infinite) and the  left and right Kronecker structures of `P(λ)`. 

The pencil based linearization is built using the methods described in [1].

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).
