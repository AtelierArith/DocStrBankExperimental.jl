```
sys = dss(R; Ts=missing, contr = false, obs = false, noseig = false, minimal = false, fast = true, atol = 0, rtol)
```

Convert the rational transfer function matrix `R(λ)` to a descriptor system representation `sys = (A-λE,B,C,D)` such that  the transfer function matrix of `sys` is `R(λ)`. The resulting `sys` is a continuous-time system if `Ts = 0` or  discrete-time system if `Ts = -1` or `Ts > 0`.  If `Ts = missing`, the sampling time of `sys` is inherited from the sampling time `TRs` of the elements of `R`, unless `TRs = nothing`,  in which case `Ts = 0` is used (by default).  

`R(λ)` is a matrix with rational transfer function entries (see [`RationalTransferFunction`](@ref) ) corresponding to a multiple-input multiple-outputs system or a rational transfer function corresponding to a single-input single-output system. The numerators and denominators of the elements of R are of type  `Polynomial` as provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

If `n` is the order of `A-λE`, then the computed realization satisfies:

(1) `A-λE` is regular and `R(λ) = C*inv(λE-A)*B+D`;

(2) `rank[B A-λE] = n` (controllability) if `minimal = true` or `contr = true`;

(3) `rank[A-λE; C] = n` (observability)  if `minimal = true` or `contr = true`;

(4) `A-λE` has no non-dynamic modes if `minimal = true` or `noseig = true`. 

If conditions (1)-(4) are satisfied, the realization is called `minimal` and the resulting order `n` is the least achievable order. If conditions (1)-(3) are satisfied, the realization is called `irreducible`  and the resulting order `n` is the least achievable order using orthogonal similarity transformations. An irreducible realization preserves the pole-zero and singular structures of `R(λ)`. 

The underlying pencil manipulation algorithms [1] and [2] to compute reduced order realizations  employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition, if `fast = false`. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The keyword arguments `atol` and `rtol`, specify the absolute and relative tolerances for the  nonzero coefficients of `R(λ)`.

[1] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[2] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017. 
