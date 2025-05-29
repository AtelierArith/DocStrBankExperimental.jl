```
prank(M::AbstractMatrix, N::AbstractMatrix; fastrank = true, atol1::Real=0, atol2::Real=0, rtol::Real=min(atol1,atol2)>0 ? 0 : n*ϵ)
```

Compute the normal rank of a matrix pencil `M - λN`. If `fastrank = true`, the rank is evaluated  by counting how many singular values of `M - γ N` have magnitude greater than `max(max(atol1,atol2), rtol*σ₁)`, where `σ₁` is the largest singular value of `M - γ N` and `γ` is a randomly generated value. If `fastrank = false`,  the rank is evaluated as `nr + ni + nf + nl`, where `nr` and `nl` are the sums of right and left Kronecker indices,  respectively, while `ni` and `nf` are the number of infinite and finite eigenvalues, respectively. The sums `nr+ni` and   `nf+nl`, are determined from an appropriate Kronecker-like form (KLF) exhibiting the spliting of the right and left structures  of the pencil `M - λN`.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `M`, the absolute tolerance for the nonzero elements of `N`,  and the relative tolerance  for the nonzero elements of `M` and `N`. The default relative tolerance is `n*ϵ`, where `n` is the size of the smallest dimension of `M`, and `ϵ` is the  machine epsilon of the element type of `M`.  For efficiency purpose, the reduction to the relevant KLF is only partially performed  using rank decisions based on rank revealing SVD-decompositions. 

!!! compat "Julia 1.1"
    The use of `atol` and `rtol` keyword arguments in rank determinations requires at least Julia 1.1.  To enforce compatibility with Julia 1.0, the newer function rank in Julia 1.1 has been explicitly included.

