```
  pmzeros2(P; fast = false, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> (val, iz, KRInfo)
```

Return the finite and infinite zeros of the polynomial matrix `P(λ)` in `val`,  the multiplicities of infinite zeros in `iz` and information on the   Kronecker-structure of the underlying irreducible descriptor system based linearization of `P(λ)` in the `KRInfo` object. 

The information on the  Kronecker-structure of the underlying linearization consists of  the right Kronecker indices `rki` (the same as of `P(λ)`), left Kronecker indices `lki` (the same as of `P(λ)`),  infinite elementary divisors `id`, the number of finite eigenvalues `nf` (the same as of `P(λ)`) and the  normal rank 'nrank', and can be obtained from `KRInfo` as  `KRInfo.rki`, `KRInfo.lki`, `KRInfo.id`, `KRInfo.nf` and `KRInfo.nrank`, respectively.  For more details, see  [`KRInfo`](@ref). 

`P(λ)` can be specified as a grade `k` polynomial matrix of the form `P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)`,  for which the coefficient matrices `P_i`, `i = 1, ..., k+1`, are stored in the 3-dimensional matrix `P`,  where `P[:,:,i]` contains the `i`-th coefficient matrix `P_i` (multiplying `λ**(i-1)`). 

`P(λ)` can also be specified as a matrix, vector or scalar of elements of the `Polynomial` type  provided by the [Polynomials](https://github.com/JuliaMath/Polynomials.jl) package.   

The computation of the zeros is performed by first building an irreducible descriptor system based  linearization of `P(λ)` [1] of order `ν` as a structured system matrix pencil 

```
          | A-λE | B | 
 M - λN = |------|---| ,
          |  C   | D |
```

such that `P(λ) = C*inv(λE-A)*B+D`, and then reducing the pencil `M-λN` to an  appropriate Kronecker-like form (KLF) which exhibits information on its Kronecker structure.   The left and right Kronecker indices of `M-λN` and `P(λ)` are the same [2] and are  returned in `KRInfo.rki` and `KRInfo.rki`, respectively. The multiplicities of the infinite zeros of `M-λN` and of `P(λ)` are the same [2] and are returned in `iz`. The number of finite zeros in `val` is equal to the number of finite eigenvalues of `M-λN`  (returned in `KRInfo.nf`), while the number of infinite zeros in `val` is the sum of multiplicites in `iz`.  The normal rank of `P(λ)` can be evaluated as `KRInfo.nrank - ν`. 

The reduction of `M-λN` to the KLF is performed using orthonal similarity transformations and involves rank decisions based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. For efficiency purposes, the reduction is only partially performed, without accumulating the performed orthogonal transformations.

The keyword arguments `atol`  and `rtol` specify the absolute and relative tolerances for the nonzero  coefficients of `P(λ)`,  respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of the smallest dimension of `P(λ)`, and `ϵ` is the  machine epsilon of the element type of coefficients of `P(λ)`. 

[1] G. Verghese, B. Levy, and T. Kailath, Generalized state-space systems, IEEE Trans. Automat. Control, 26:811-831 (1981).

[2] G. Verghese, Comments on ‘Properties of the system matrix of a generalized state-space system’, Int. J. Control, Vol.31(5) (1980) 1007–1009.
