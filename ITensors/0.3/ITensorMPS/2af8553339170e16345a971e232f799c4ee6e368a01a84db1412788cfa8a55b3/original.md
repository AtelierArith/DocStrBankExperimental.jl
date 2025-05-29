```
inner(A::MPS, B::MPS)
inner(A::MPO, B::MPO)
```

Compute the inner product `⟨A|B⟩`. If `A` and `B` are MPOs, computes the Frobenius inner product.

Use [`loginner`](@ref) to avoid underflow/overflow for taking overlaps of large MPS or MPO.

!!! compat "ITensors 0.3"



Before ITensors 0.3, `inner` had a keyword argument `make_inds_match` that default to `true`.   When true, the function attempted to make the site indices match before contracting. So for example, the   inputs could have different site indices, as long as they have the same dimensions or QN blocks.   This behavior was fragile since it only worked for MPS with single site indices per tensor,   and as of ITensors 0.3 has been deprecated. As of ITensors 0.3 you will need to make sure   the MPS or MPO you input have compatible site indices to contract over, such as by making   sure the prime levels match properly.

Same as [`dot`](@ref).

See also [`loginner`](@ref), [`logdot`](@ref).
