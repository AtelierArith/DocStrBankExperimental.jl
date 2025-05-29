```
  rm2ls(NUM, DEN; contr = false, obs = false, noseig = false, minimal = false,
        fast = true, atol = 0, rtol) -> (A, E, B, C, D, blkdims)
```

Build a structured linearization as a system matrix `S(λ)` of the form

```
           | A-λE | B | 
    S(λ) = |------|---|
           |  C   | D |
```

for the rational matrix `R(λ) = NUM(λ) ./ DEN(λ)`, such that `S(λ)` preserves a part of the Kronecker structure of `R(λ)`.  The regular pencil `A-λE` has the block diagonal form

```
         | Af-λI |   0   | 
  A-λE = |-------|-------|
         |  0    | I-λEi |
```

and the dimensions of the diagonal blocks `Af` and `Ei` are provided in `blkdims[1]` and `blkdims[2]`, respectively.

`NUM(λ)` is a polynomial matrix of the form `NUM(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)`, for which   the coefficient matrices `N_i`, `i = 1, ..., k+1` are stored in the 3-dimensional matrix `NUM`,  where `NUM[:,:,i]` contains the `i`-th coefficient matrix `N_i` (multiplying `λ**(i-1)`). 

`DEN(λ)` is a polynomial matrix of the form `DEN(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)`, for which  the coefficient matrices `D_i`, `i = 1, ..., l+1`, are stored in the 3-dimensional matrix `DEN`,  where `DEN[:,:,i]` contain the `i`-th coefficient matrix `D_i` (multiplying `λ**(i-1)`). 

Alternatively, `NUM(λ)` and `DEN(λ)` can be specified as matrices of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.  In this case, no check is performed that `N(λ)` and `D(λ)` have the same indeterminates.

If `n` is the order of `A-λE`, then the computed linearization satisfies:

(1) `A-λE` is regular and `R(λ) = C*inv(λE-A)*B+D`;

(2) `rank[B A-λE] = n` (controllability) if `minimal = true` or `contr = true`, in which case  the right Kronecker structure is preserved;

(3) `rank[A-λE; C] = n` (observability)  if `minimal = true` or `obs = true`, in which case  the left Kronecker structure is preserved;

(4) `A-λE` has no non-dynamic modes if `minimal = true` or `noseig = true`. 

If conditions (1)-(4) are satisfied, the linearization is called `minimal` and the resulting order `n` is the least achievable order. If conditions (1)-(3) are satisfied, the linearization is called `irreducible`  and the resulting order `n` is the least achievable order using orthogonal similarity transformations. For an irreducible linearization `S(λ)` preserves the pole-zero structure (finite and infinite) and the  left and right Kronecker structures of `R(λ)`. 

The descriptor system based linearization is built using the methods described in [1] in conjunction with pencil manipulation algorithms [2] and [3] to compute reduced order linearizations. These algorithms  employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition, if `fast = false`. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The keyword arguments `atol` and `rtol`, specify the absolute and relative tolerances, respectively, for the  nonzero coefficients of `NUM(λ)` and `DEN(λ)`.

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).

[2] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[3] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017. 
