```
pmkstruct(P; CF1, grade=l, fast = false, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> KRInfo, iz, ip
```

Determine the Kronecker-structure and infinite pole-zero structure information of the polynomial matrix `P(λ)` and  return an `KRInfo` object and the multiplicities of infinite zeros and poles.  The computation of the Kronecker-structure employs strong linearizations of `P(λ)` in either  the first companion form, if `CF1 = true`, or the second companion form, if `CF1 = false`.  The effective grade `l` to be used for linearization can be specified via the keyword argument `grade` as  `grade = l`, where `l` must be chosen equal to or greater than the degree of `P(λ)`.  The default value used for `l` is `l = deg(P(λ))`.

`P(λ)` can be specified as a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`,  for which the coefficient matrices `P_i`, `i = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`). 

`P(λ)` can also be specified as a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

The information on the Kronecker-structure consists of the right Kronecker indices `rki`,  left Kronecker indices `lki`, infinite elementary divisors `id`, the number of finite eigenvalues `nf` and normal rank `nrank` and can be obtained from `KRInfo` as  `KRInfo.rki`, `KRInfo.lki`, `KRInfo.id`, `KRInfo.nf` and `KRInfo.nrank`, respectively.  For more details, see  [`KRInfo`](@ref). 

The determination of the Kronecker-structure information is performed by building a companion  form linearization `M-λN` of `P(λ)` and reducing the pencil `M-λN` to an  appropriate Kronecker-like form (KLF) which exhibits the number of finite eigenvalues,  the multiplicities of the infinite eigenvalues,  the left and right Kronecker indices and the normal rank. The Kronecker-structure information and pole-zero stucture information on `P(λ)` are recovered from  the Kronecker-structure information on `M-λN` using the results of [1] and [2].

The right Kronecker indices are provided in the integer vector `rki`.  The number of elements of `rki` is the dimension of the right nullspace of the polynomial matrix `P(λ)`  and their sum is the least degree of a right polynomial nullspace basis. 

The left Kronecker indices are provided in the integer vector `lki`.  The number of elements of `lki` is the dimension of the left nullspace of the polynomial matrix `P(λ)`  and their sum is the least degree of a left polynomial nullspace basis. 

The multiplicities of infinite eigenvalues are provided in the integer vector `id`,  where each `i`-th element `id[i]` is the order of an infinite elementary divisor  (i.e., the multiplicity of an infinite eigenvalue).   

The multiplicities of the infinite zeros of `P(λ)` are returned in `iz` and represent  the positive differences between the multiplicities of  the infinite eigenvalues of `P(λ)` and the effective grade `l` of `P(λ)` [2]. 

The multiplicities of the infinite poles of `P(λ)` are returned in `ip` and represent  the absolute values of the negative differences between the multiplicities of  the infinite eigenvalues of `P(λ)` and the effective grade `l` of `P(λ)` [2]. 

The reduction to the KLF is performed using orthogonal similarity transformations and involves rank decisions based  on rank revealing QR-decompositions with column pivoting, if `fast = true`, or, the more reliable,  SVD-decompositions, if `fast = false`. 

The keyword arguments `atol`  and `rtol` specify the absolute and relative tolerances for the nonzero  coefficients of `P(λ)`,  respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of the smallest dimension of `P(λ)`, and `ϵ` is the  machine epsilon of the element type of coefficients of `P(λ)`. 

[1] F. De Terán, F. M. Dopico, D. S. Mackey, Spectral equivalence of polynomial matrices and the Index Sum Theorem, Linear Algebra and Its Applications, vol. 459, pp. 264-333, 2014.

[2] A. Varga, On computing the Kronecker structure of polynomial matrices using Julia, June 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).
