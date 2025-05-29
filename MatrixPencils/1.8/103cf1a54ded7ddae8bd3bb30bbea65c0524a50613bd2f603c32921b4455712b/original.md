```
rmpoles1(N, D;  fast = false, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> (val, ip, id)
```

Return the finite and infinite poles of the rational matrix `R(λ) := N(λ)./D(λ)`  in `val`,  the multiplicities of infinite poles in `ip` and the infinite elementary divisors of the pole pencil  of the underlying strongly irreducible pencil based linearization of  `R(λ)` in `id`.

The information on the finite and infinite poles of the rational matrix `R(λ)` is obtained from the  pole-structure information of the underlying pencil based linearization using the results of [1] and [2].  The determination of the pole-structure information is performed by building a strongly minimal  pencil based linearization `(A-λE,B-λF,C-λG,D-λH)` with `A-λE` a regular pencil of order `n`,  satisfying `R(λ) = (C-λG)*inv(λE-A)*(B-λF)+D-λH` and reducing the structured system matrix pencil  `Sp(λ) = [A-λE -λF; -λG -λH]` to an appropriate Kronecker-like form (KLF) which exhibits  the number of its finite eigenvalues (also the finite poles of `R(λ)`) and the multiplicities of the  infinite eigenvalues (in excess with one to the multiplicities of infinite poles of `R(λ)`). The multiplicities of the infinite zeros of `Sp(λ)` and of infinite poles of `R(λ)` are the same [2]  and are returned in `ip`. The number of infinite poles in `val` is equal to the sum of multiplicites in `ip`.  The multiplicities of the infinite eigenvalues of `Sp(λ)` are returned in `id`.

The numerator `N(λ)` is a polynomial matrix of the form `N(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)`,    for which the coefficient matrices `N_i`, `i = 1, ..., k+1` are stored in the 3-dimensional matrix `N`,  where `N[:,:,i]` contains the `i`-th coefficient matrix `N_i` (multiplying `λ**(i-1)`). 

The denominator `D(λ)` is a polynomial matrix of the form `D(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)`,   for which the coefficient matrices `D_i`, `i = 1, ..., l+1`, are stored in the 3-dimensional matrix `D`,  where `D[:,:,i]` contain the `i`-th coefficient matrix `D_i` (multiplying `λ**(i-1)`). 

Alternatively, `N(λ)` and `D(λ)` can be specified as matrices of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.  In this case, no check is performed that `N(λ)` and `D(λ)` have the same indeterminates.

The strongly minimal pencil based linearization is built using the methods described in [3] in conjunction with pencil manipulation algorithms of [4] to compute reduced order linearizations. These algorithms  employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition, if `fast = false`. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The reduction of `Sp(λ)` to the KLF is performed using orthonal similarity transformations [5] and involves rank decisions  based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. For efficiency purposes, the reduction is only partially performed, without accumulating the performed orthogonal transformations.

The keyword arguments `atol`  and `rtol` specify the absolute and relative tolerances,  respectively, for the nonzero  coefficients of `N(λ)` and `D(λ)`.  The default relative tolerance is `n*ϵ`, where `n` is the size of the smallest dimension of `N(λ)`, and `ϵ` is the  machine epsilon of the element type of coefficients of `N(λ)`. 

[1] G. Verghese, B. Levy, and T. Kailath, Generalized state-space systems, IEEE Trans. Automat. Control, 26:811-831 (1981).

[2] G. Verghese, Comments on ‘Properties of the system matrix of a generalized state-space system’, Int. J. Control, Vol.31(5) (1980) 1007–1009.

[3] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).

[4] F.M. Dopico, M.C. Quintana and P. Van Dooren, Linear system matrices of rational transfer functions, to appear in "Realization and Model Reduction of Dynamical Systems",  A Festschrift to honor the 70th birthday of Thanos Antoulas", Springer-Verlag. [arXiv:1903.05016](https://arxiv.org/pdf/1903.05016.pdf)

[5] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017. 
