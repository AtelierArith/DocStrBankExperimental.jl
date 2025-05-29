```
lambertw(z::Complex{T}, k::V=0) where {T<:Real, V<:Integer}
lambertw(z::T, k::V=0) where {T<:Real, V<:Integer}
```

Compute the `k`th branch of the Lambert W function of `z`. If `z` is real, `k` must be either `0` or `-1`. For `Real` `z`, the domain of the branch `k = -1` is `[-1/e, 0]` and the domain of the branch `k = 0` is `[-1/e, Inf]`. For `Complex` `z`, and all `k`, the domain is the complex plane.

```jldoctest
julia> lambertw(-1/e, -1)
-1.0

julia> lambertw(-1/e, 0)
-1.0

julia> lambertw(0, 0)
0.0

julia> lambertw(0, -1)
-Inf

julia> lambertw(Complex(-10.0, 3.0), 4)
-0.9274337508660128 + 26.37693445371142im
```
