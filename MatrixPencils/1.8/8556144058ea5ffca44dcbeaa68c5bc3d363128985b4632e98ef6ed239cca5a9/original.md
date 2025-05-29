```
spzeros(A, E, B, C, D; fast = false, atol1::Real = 0, atol2::Real = 0, rtol::Real=min(atol1,atol2)>0 ? 0 : n*ϵ) -> (val, iz, KRInfo)
```

Return the (finite and infinite) Smith zeros of the structured matrix pencil `M-λN` 

```
          | A-λE | B | 
 M - λN = |------|---|
          |  C   | D |
```

in `val`, information on the multiplicities of infinite zeros in `iz` and   information on the Kronecker-structure in the `KRInfo` object. 

The information on the multiplicities of infinite zeros is provided in the vector `iz`,  where each `i`-th element `iz[i]` is equal to `k-1`, where `k` is the order of an infinite elementary divisor with `k > 0`. The number of infinite zeros contained in `val` is the sum of the components of `iz`. 

The information on the Kronecker-structure consists of the right Kronecker indices `rki`, left Kronecker indices `lki`,  infinite elementary divisors `id`, the number of finite eigenvalues `nf`, the normal rank `nrank`, and can be obtained  from `KRInfo` as `KRInfo.rki`, `KRInfo.lki`, `KRInfo.id`, `KRInfo.nf` and `KRInfo.nrank`, respectively.  For more details, see  [`pkstruct`](@ref). 

The computation of the zeros is performed by reducing the pencil `M-λN` to an appropriate Kronecker-like form (KLF)  which exhibits the splitting of the infinite and finite eigenvalue,  the multiplicities of the infinite eigenvalues, the left and right Kronecker indices and the normal rank. The reduction is performed using orthonal similarity transformations and involves rank decisions based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. For efficiency purposes, the reduction is only partially performed, without accumulating the performed orthogonal transformations.

The keyword arguments `atol1`, `atol2`  and `rtol` specify the absolute tolerance for the nonzero elements of `M`, the absolute tolerance for the nonzero elements of `N`, and the relative tolerance for the nonzero elements of `M` and `N`, respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of the smallest dimension of `M`, and `ϵ` is the  machine epsilon of the element type of `M`. 
