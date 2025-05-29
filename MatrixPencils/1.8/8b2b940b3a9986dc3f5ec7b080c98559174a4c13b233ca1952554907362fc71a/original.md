```
rmpoles(N, D; fast = false, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> (val, ip, id)
```

Return the finite and infinite poles of the rational matrix `R(λ) := N(λ)./D(λ)`  in `val`,  the multiplicities of infinite poles in `ip` and the infinite elementary divisors of the pole pencil  of the underlying irreducible descriptor system based linearization of `R(λ)` in `id`.

The information on the finite and infinite poles of the rational matrix `R(λ)` is obtained from the  Kronecker-structure information of the underlying linearization using the results of [1] and [2].  The determination of the Kronecker-structure information is performed by building an irreducible  descriptor system realization `(A-λE,B,C,D)` with `A-λE` a regular pencil of order `n`,  satisfying `R(λ) = C*inv(λE-A)*B+D` and reducing the regular pencil `A-λE`  to an appropriate Kronecker-like form (KLF) which exhibits  the its finite eigenvalues (also the finite poles of `R(λ)`) and the multiplicities of the  infinite eigenvalues (in excess with one to the multiplicities of infinite poles of `R(λ)`). The multiplicities of the infinite zeros of `A-λE` and of infinite poles of `R(λ)` are the same [2]  and are returned in `ip`. The number of infinite poles in `val` is equal to the sum of multiplicites in `ip`.  The multiplicities of the infinite eigenvalues of `A-λE` are returned in `id`.

The numerator `N(λ)` is a polynomial matrix of the form `N(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)`,    for which the coefficient matrices `N_i`, `i = 1, ..., k+1` are stored in the 3-dimensional matrix `N`,  where `N[:,:,i]` contains the `i`-th coefficient matrix `N_i` (multiplying `λ**(i-1)`). 

The denominator `D(λ)` is a polynomial matrix of the form `D(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)`,   for which the coefficient matrices `D_i`, `i = 1, ..., l+1`, are stored in the 3-dimensional matrix `D`,  where `D[:,:,i]` contain the `i`-th coefficient matrix `D_i` (multiplying `λ**(i-1)`). 

Alternatively, `N(λ)` and `D(λ)` can be specified as matrices of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.  In this case, no check is performed that `N(λ)` and `D(λ)` have the same indeterminates.

The irreducible descriptor system based linearization is built using the methods described in [3] in conjunction with pencil manipulation algorithms of [4] and [5] to compute reduced order linearizations. These algorithms  employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition, if `fast = false`. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The reduction of `A-λE` to the KLF is performed using orthonal similarity transformations and involves rank decisions  based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. For efficiency purposes, the reduction is only partially performed, without accumulating the performed orthogonal transformations.

The keyword arguments `atol`  and `rtol` specify the absolute and relative tolerances for the nonzero  coefficients of `N(λ)` and `D(λ)`,  respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of the smallest dimension of `N(λ)`, and `ϵ` is the  machine epsilon of the element type of coefficients of `N(λ)`. 

[1] G. Verghese, B. Levy, and T. Kailath, Generalized state-space systems, IEEE Trans. Automat. Control, 26:811-831 (1981).

[2] G. Verghese, Comments on ‘Properties of the system matrix of a generalized state-space system’, Int. J. Control, Vol.31(5) (1980) 1007–1009.

[3] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).

[4] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[5] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017. 
