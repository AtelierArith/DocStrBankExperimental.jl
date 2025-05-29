```
 spm2lps(T, U, V, W; fast = true, contr = false, obs = false, minimal = false, atol = 0, rtol) -> (A, E, B, F, C, G, D, H)
```

Build a structured linearization 

```
          | A-λE | B-λF | 
 M - λN = |------|------|
          | C-λG | D-λH |
```

of the structured polynomial matrix 

```
          | -T(λ) | U(λ) |
   P(λ) = |-------|------|
          |  V(λ) | W(λ) |
```

such that `V(λ)*inv(T(λ))*U(λ)+W(λ) = (C-λG))*inv(λE-A)*(B-λF)+D-λH`. The resulting linearization `M - λN` preserves a part,  if `minimal = false`, or the complete Kronecker structure, if `minimal = true`, of `P(λ)`. In the latter case,  the order `n` of `A-λE` is the least possible one and `M - λN` is a strong linearization of `P(λ)`.

`T(λ)`, `U(λ)`, `V(λ)`, and `W(λ)` can be specified as polynomial matrices of the form `X(λ) = X_1 + λ X_2 + ... + λ**k X_(k+1)`,  for `X = T`, `U`, `V`, and `W`, for which the coefficient matrices `X_i`, `i = 1, ..., k+1`, are stored in  the 3-dimensional matrices `X`, where `X[:,:,i]` contains the `i`-th coefficient matrix `X_i` (multiplying `λ**(i-1)`). 

`T(λ)`, `U(λ)`, `V(λ)`, and `W(λ)` can also be specified as matrices, vectors or scalars of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

The computed structured linearization satisfies:

(1) `A-λE` is regular;

(2) `rank[B-λF A-λE] = n` (strong controllability) if `minimal = true` or `contr = true`, in which case  the finite and right Kronecker structures are preserved;

(3) `rank[A-λE; C-λG] = n` (strong observability)  if `minimal = true` or `obs = true`, in which case  the finite and left Kronecker structures are preserved.

The keyword arguments `atol` and `rtol`, specify, respectively, the absolute and relative tolerance for the  nonzero coefficients of the matrices `T(λ)`, `U(λ)`, `V(λ)` and `W(λ)`. The default relative tolerance is `nt*ϵ`,  where `nt` is the size of the square matrix `T(λ)` and `ϵ` is the machine epsilon of the element type of its coefficients. 
