```
   rmrank(N, D; fastrank = true, atol = 0, rtol = atol > 0 ? 0 : n*ϵ)
```

Determine the normal rank of the rational matrix `R(λ) := N(λ)./D(λ)`.

If `fastrank = true`, the rank is evaluated by counting how many singular values of `R(γ)` have magnitude greater  than `max(atol, rtol*σ₁)`, where `σ₁` is the largest singular value of `R(γ)` and `γ` is a randomly generated  complex value of magnitude equal to one.  If `fastrank = false`, first a structured linearization of `R(λ)` is built in the form of a descriptor system matrix  `S(λ) = [A-λE B; C D]` with `A-λE` an order `n` regular subpencil, and then its normal rank `nr` is determined.  The normal rank of `R(λ)` is `nr - n`.   

The numerator `N(λ)` is a polynomial matrix of the form `N(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)`,    for which the coefficient matrices `N_i`, `i = 1, ..., k+1` are stored in the 3-dimensional matrix `N`,  where `N[:,:,i]` contains the `i`-th coefficient matrix `N_i` (multiplying `λ**(i-1)`). 

The denominator `D(λ)` is a polynomial matrix of the form `D(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)`,   for which the coefficient matrices `D_i`, `i = 1, ..., l+1`, are stored in the 3-dimensional matrix `D`,  where `D[:,:,i]` contain the `i`-th coefficient matrix `D_i` (multiplying `λ**(i-1)`). 

Alternatively, `N(λ)` and `D(λ)` can be specified as matrices of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.  In this case, no check is performed that `N(λ)` and `D(λ)` have the same indeterminates.

The irreducible descriptor system based linearization is built using the methods described in [1] in conjunction with pencil manipulation algorithms of [2] and [3] to compute reduced order linearizations. These algorithms  employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition, if `fast = false`. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The reduction to the appropriate KLF of `S(λ)` is performed using orthogonal similarity transformations [3] and involves rank decisions based on rank revealing SVD-decompositions. 

The keyword arguments `atol`  and `rtol` specify the absolute and relative tolerances for the nonzero  coefficients of `N(λ)` and `D(λ)`,  respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of the smallest dimension of `N(λ)`, and `ϵ` is the  machine epsilon of the element type of coefficients of `N(λ)`. 

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).

[2] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[3] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017. 
