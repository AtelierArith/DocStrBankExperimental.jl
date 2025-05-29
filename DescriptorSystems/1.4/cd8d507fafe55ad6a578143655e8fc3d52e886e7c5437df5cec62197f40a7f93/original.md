```
sys = dss(T, U, V, W; fast = true, contr = false, obs = false, minimal = false, atol = 0, rtol)
```

Construct an input-output equivalent descriptor system representation `sys = (A-λE,B,C,D)`  to a polynomial model specified by the polynomial matrices `T(λ)`, `U(λ)`, `V(λ)`, and `W(λ)` such that 

```
  V(λ)*inv(T(λ))*U(λ)+W(λ) = C*inv(λE-A)*B+D.
```

If `minimal = true`, the resulting realization `(A-λE,B,C,D)` has the least possible order `n` of `A-λE`. 

`T(λ)`, `U(λ)`, `V(λ)`, and `W(λ)` can be specified as polynomial matrices of the form `X(λ) = X_1 + λ X_2 + ... + λ**k X_(k+1)`,  for `X = T`, `U`, `V`, and `W`, for which the coefficient matrices `X_i`, `i = 1, ..., k+1`, are stored in  the 3-dimensional matrices `X`, where `X[:,:,i]` contains the `i`-th coefficient matrix `X_i` (multiplying `λ**(i-1)`). 

`T(λ)`, `U(λ)`, `V(λ)`, and `W(λ)` can also be specified as matrices, vectors or scalars of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.    In this case, no check is performed that `T(λ)`, `U(λ)`, `V(λ)`  and `W(λ)` have the same indeterminates.

The computed descriptor realization satisfies:

(1) `A-λE` is regular;

(2) `rank[B A-λE] = n` (controllability) if `minimal = true` or `contr = true`;

(3) `rank[A-λE; C] = n` (observability)  if `minimal = true` or `obs = true`;

(4) `A-λE` has no simple infinite eigenvalues if `minimal = true`.

The keyword arguments `atol` and `rtol`, specify, respectively, the absolute and relative tolerance for the  nonzero coefficients of the matrices `T(λ)`, `U(λ)`, `V(λ)` and `W(λ)`. The default relative tolerance is `nt*ϵ`,  where `nt` is the size of the square matrix `T(λ)` and `ϵ` is the machine epsilon of the element type of its coefficients. 

The descriptor realization is built using the methods described in [1].

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).
