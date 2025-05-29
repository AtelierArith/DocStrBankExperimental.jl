```julia
twonorm(
    v::AbstractVector{Float64},
    M::AbstractMatrix{Float64}
) -> Any

```

Implementation of the discrete $L^2$-norm based on a mass matrix. Faster version of pnorm for p=2 by using that direct assembly of mass matrix instead of basis matrices is possible. Can be used for domain or boundary depending on the respective mass matrix.
