```
spkstruct(A, E, B, C, D; fast = false, atol1::Real = 0, atol2::Real = 0, rtol::Real=min(atol1,atol2)>0 ? 0 : n*ϵ) -> KRInfo
```

Determine the Kronecker-structure information of the structured matrix pencil `M-λN` 

```
          | A-λE | B | 
 M - λN = |------|---|
          |  C   | D |
```

and return an `KRInfo` object. 

The information on the  Kronecker-structure consists of the right Kronecker indices `rki`, left Kronecker indices `lki`,  infinite elementary divisors `id`, the number of finite eigenvalues `nf`, the normal rank `nrank`, and can be obtained  from `KRInfo` as `KRInfo.rki`, `KRInfo.lki`, `KRInfo.id`, `KRInfo.nf` and `KRInfo.nrank`, respectively.  For more details, see  [`pkstruct`](@ref). 

The right Kronecker indices are provided in the integer vector `rki`, where each `i`-th element `rki[i]` is  the row dimension `k` of an elementary Kronecker block of size `k x (k+1)`.  The number of elements of `rki` is the dimension of  the right nullspace of the pencil `M-λN` and their sum is the least degree of a right polynomial nullspace basis. 

The left Kronecker indices are provided in the integer vector `lki`, where each `i`-th element `lki[i]` is  the column dimension `k` of an elementary Kronecker block of size `(k+1) x k`.  The number of elements of `lki` is the dimension of  the left nullspace of the pencil `M-λN` and their sum is the least degree of a left polynomial nullspace basis. 

The multiplicities of infinite eigenvalues are provided in the integer vector `id`, where each `i`-th element `id[i]` is the order of an infinite elementary divisor (i.e., the multiplicity of an infinite eigenvalue). 

The determination of the Kronecker-structure information is performed by reducing the pencil `M-λN` to an  appropriate Kronecker-like form (KLF) which exhibits the number of finite eigenvalues,  the multiplicities of the infinite eigenvalues, the left and right Kronecker indices and the normal rank. The reduction is performed using orthonal similarity transformations and involves rank decisions based  on rank revealing QR-decompositions with column pivoting, if `fast = true`, or, the more reliable,  SVD-decompositions, if `fast = false`. For efficiency purposes, the reduction is only partially performed, without accumulating the performed orthogonal transformations. 

The keyword arguements `atol1`, `atol2`  and `rtol` specify the absolute tolerance for the nonzero elements of `M`, the absolute tolerance for the nonzero elements of `N`, and the relative tolerance for the nonzero elements of `M` and `N`, respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of the smallest dimension of `M`, and `ϵ` is the  machine epsilon of the element type of `M`. 
