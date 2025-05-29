```
pkstruct(M, N; fast = false, atol1::Real = 0, atol2::Real = 0, rtol::Real=min(atol1,atol2)>0 ? 0 : n*ϵ) -> KRInfo
```

Determine the Kronecker-structure information of the matrix pencil `M-λN` and return an `KRInfo` object. 

The right Kronecker indices `rki`, left Kronecker indices `lki`, infinite elementary divisors `id`, the number of finite eigenvalues `nf` and the normal rank `nrank` can be obtained from  `KRInfo` as `KRInfo.rki`, `KRInfo.lki`, `KRInfo.id`, `KRInfo.nf` and `KRInfo.nrank`, respectively.   The determination of the Kronecker-structure information is performed by reducing the pencil `M-λN` to an  appropriate Kronecker-like form (KLF) exhibiting all structural elements of the pencil `M-λN`. The reduction is performed using orthogonal similarity transformations and involves rank decisions based  on rank revealing QR-decompositions with column pivoting, if `fast = true`, or, the more reliable,  SVD-decompositions, if `fast = false`. For efficiency purposes, the reduction is only partially performed, without accumulating the performed orthogonal transformations. 

The right Kronecker indices are provided in the integer vector `rki`, where each `i`-th element `rki[i]` is  the row dimension `k` of an elementary Kronecker block of size `k x (k+1)`.  The number of elements of `rki` is the dimension of  the right nullspace of the pencil `M-λN` and their sum is the degree of a right minimal polynomial nullspace basis. 

The left Kronecker indices are provided in the integer vector `lki`, where each `i`-th element `lki[i]` is  the column dimension `k` of an elementary Kronecker block of size `(k+1) x k`.  The number of elements of `lki` is the dimension of  the left nullspace of the pencil `M-λN` and their sum is the degree of a left minimal polynomial nullspace basis. 

The multiplicities of infinite eigenvalues are provided in the integer vector `id`, where each `i`-th element `id[i]` is the order of an infinite elementary divisor (i.e., the multiplicity of an infinite eigenvalue).   The number of elements of `id` is the number of infinite elementary divisors of the pencil `M-λN`. 

The normal rank `nrank` is the maximum rank of `M-λN` for all values of `λ`. If `N = nothing`, then `nrank` is the rank of `M`.  

The keyword arguements `atol1`, `atol2`  and `rtol` specify the absolute tolerance for the nonzero elements of `M`, the absolute tolerance for the nonzero elements of `N`, and the relative tolerance for the nonzero elements of `M` and `N`, respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of the smallest dimension of `M`, and `ϵ` is the  machine epsilon of the element type of `M`. 
