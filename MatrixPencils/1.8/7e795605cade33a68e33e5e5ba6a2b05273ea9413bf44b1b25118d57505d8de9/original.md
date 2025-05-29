```
 pm2ls(P; contr = false, obs = false, noseig = false, minimal = false,
          fast = true, atol = 0, rtol) -> (A, E, B, C, D)
```

Build a structured linearization as a system matrix `S(λ)` of the form

```
        | A-λE | B | 
 S(λ) = |------|---|
        |  C   | D |
```

of the polynomial matrix `P(λ)` which preserves a part of the Kronecker structure of `P(λ)`. 

`P(λ)` can be specified as a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`,  for which the coefficient matrices `P_i`, `i = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`). 

`P(λ)` can also be specified as a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

If `d` is the degree of `P(λ)` and `n` is the order of `A-λE`, then the computed linearization satisfies:

(1) `A-λE` is regular and `P(λ) = C*inv(λE-A)*B+D`;

(2) `rank[B A-λE] = n` (controllability) if `minimal = true` or `contr = true`, in which case  the right Kronecker structure is preserved;

(3) `rank[A-λE; C] = n` (observability)  if `minimal = true` or `contr = true`, in which case  the left Kronecker structure is preserved;

(4) `A-λE` has no non-dynamic modes if `minimal = true` or `noseig = true`. 

If conditions (1)-(4) are satisfied, the linearization is called `minimal` and the resulting order `n` is the least achievable order. If conditions (1)-(3) are satisfied, the linearization is called `irreducible`  and the resulting order `n` is the least achievable order using orthogonal similarity transformations. For an irreducible linearization `S(λ)` preserves the pole-zero structure (finite and infinite) and the  left and right Kronecker structures of `P(λ)`. 

The underlying pencil manipulation algorithms [1] and [2] to compute reduced order linearizations  employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition, if `fast = false`. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The keyword arguments `atol` and `rtol`, specify the absolute and relative tolerances for the  nonzero coefficients of `P(λ)`, respectively.

[1] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[2] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017. 
