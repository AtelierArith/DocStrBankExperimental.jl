```
inner(B::MPO, y::MPS, A::MPO, x::MPS)
```

Compute `⟨By|A|x⟩ = ⟨By|Ax⟩` efficiently and exactly without making any intermediate MPOs. In general it is more efficient and accurate than `inner(apply(B, y), apply(A, x))`.

This is helpful for computing the variance of an operator `A`, which would be:

```julia
inner(A, x, A, x) - inner(x, A, x) ^ 2
```

!!! compat "ITensors 0.3"



Before ITensors 0.3, `inner` had a keyword argument `make_inds_match` that default to `true`.   When true, the function attempted to make the site indices match before contracting. So for example, the   inputs could have different site indices, as long as they have the same dimensions or QN blocks.   This behavior was fragile since it only worked for MPS with single site indices per tensor,   and as of ITensors 0.3 has been deprecated. As of ITensors 0.3 you will need to make sure   the MPS or MPO you input have compatible site indices to contract over, such as by making   sure the prime levels match properly.

Same as [`dot`](@ref).
