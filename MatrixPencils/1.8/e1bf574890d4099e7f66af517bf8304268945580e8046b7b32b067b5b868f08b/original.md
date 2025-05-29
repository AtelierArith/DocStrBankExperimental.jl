```
pmeigvals(P; CF1, grade = l, fast = false, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> (val, KRInfo)
```

Return the finite and infinite eigenvalues of the polynomial matrix `P(λ)` in `val`  and information on the Kronecker-structure of `P(λ)` in the `KRInfo` object.  The computation of eigenvalues and Kronecker-structure employs strong linearizations of `P(λ)` in either  the first companion form, if `CF1 = true`, or the second companion form, if `CF1 = false`.  The effective grade `l` to be used for linearization can be specified via the keyword argument `grade` as  `grade = l`, where `l` must be chosen equal to or greater than the degree of `P(λ)`.

`P(λ)` can be specified as a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`,  for which the coefficient matrices `P_i`, `i = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`). 

`P(λ)` can also be specified as a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

The information on the Kronecker-structure consists of the right Kronecker indices `rki`,  left Kronecker indices `lki`, infinite elementary divisors `id`, the number of finite eigenvalues `nf` and normal rank `nrank` and can be obtained from `KRInfo` as  `KRInfo.rki`, `KRInfo.lki`, `KRInfo.id`, `KRInfo.nf` and `KRInfo.nrank`, respectively. For more details, see  [`KRInfo`](@ref). 

The computation of the eigenvalues is performed by building the companion form based linearization `M-λN`  of the polynomial matrix `P(λ)` and then reducing the pencil `M-λN` to an appropriate Kronecker-like form (KLF)  which exhibits the number of finite eigenvalues, the multiplicities of the infinite eigenvalues,  the left and right Kronecker indices and the normal rank.  The left and right Kronecker indices of `P(λ)` are returned in `KRInfo.rki` and `KRInfo.rki`, respectively, and  their values are recovered from the left and right Kronecker indices of `M-λN` using the results of [1]. The multiplicities of the infinite eigenvalues of `P(λ)` of effective grade `l` is returned in `KRInfo.id`.  The number of finite eigenvalues in `val` is equal to the number of finite eigenvalues of `M-λN` (returned in `KRInfo.nf`),  while the number of infinite eigenvalues in `val` is the sum of multiplicites returned in `KRInfo.id`. 

The reduction of `M-λN` to the KLF is performed using orthonal similarity transformations and involves rank decisions  based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. For efficiency purposes, the reduction is only partially performed, without accumulating the performed orthogonal transformations.

The keyword arguments `atol`  and `rtol` specify the absolute and relative tolerances for the nonzero  coefficients of `P(λ)`,  respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of the smallest dimension of `P(λ)`, and `ϵ` is the  machine epsilon of the element type of coefficients of `P(λ)`. 

[1] F. De Terán, F. M. Dopico, D. S. Mackey, Spectral equivalence of polynomial matrices and the Index Sum Theorem, Linear Algebra and Its Applications, vol. 459, pp. 264-333, 2014.
