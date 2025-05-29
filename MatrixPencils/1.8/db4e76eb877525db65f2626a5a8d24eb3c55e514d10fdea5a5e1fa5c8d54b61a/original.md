```
pmpoles2(P; fast = false, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> (val, ip, id)
```

Return the infinite poles of the polynomial matrix `P(λ)` in `val`,  the multiplicities of infinite poles in `ip` and the infinite elementary divisors of the pole pencil  of the underlying irreducible descriptor system based linearization of `P(λ)` in `id`.

`P(λ)` can be specified as a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`,  for which the coefficient matrices `P_i`, `i = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`). 

`P(λ)` can also be specified as a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.  

The information on the infinite poles of the polynomial matrix `P(λ)` is obtained from the  pole-structure information of the underlying linearization using the results of [1] and [2].  The determination of the pole-structure information is performed by building an irreducible  descriptor system realization `(A-λE,B,C,D)` with `A-λE` unimodular,  satisfying `R(λ) = C*inv(λE-A)*B+D` and reducing the pole pencil `A-λE`  to an appropriate Kronecker-like form (KLF) which exhibits  the multiplicities of the infinite eigenvalues (in excess with one to the multiplicities of infinite poles of `P(λ)`). The multiplicities of the infinite zeros of `A-λE` and of infinite poles of `P(λ)` are the same [2]  and are returned in `ip`. The number of infinite poles in `val` is equal to the sum of multiplicites in `ip`.  The multiplicities of the infinite eigenvalues of `A-λE` are returned in `id`.

The reduction of `A-λE` to the KLF is performed using orthonal similarity transformations and involves rank decisions  based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. For efficiency purposes, the reduction is only partially performed, without accumulating the performed orthogonal transformations.

The keyword arguments `atol`  and `rtol` specify the absolute and relative tolerances for the nonzero  coefficients of `P(λ)`,  respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of the smallest dimension of `P(λ)`, and `ϵ` is the  machine epsilon of the element type of coefficients of `P(λ)`. 

[1] G. Verghese, B. Levy, and T. Kailath, Generalized state-space systems, IEEE Trans. Automat. Control, 26:811-831 (1981).

[2] G. Verghese, Comments on ‘Properties of the system matrix of a generalized state-space system’, Int. J. Control, Vol.31(5) (1980) 1007–1009.
