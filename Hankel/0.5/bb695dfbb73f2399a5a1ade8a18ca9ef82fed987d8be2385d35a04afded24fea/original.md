```
onaxis(Ak, Q::QDHT; dim=Q.dim)
```

Calculate on-axis sample in space (i.e. at r=0) from transformed array `Ak`.

!!! note
    `onaxis` is currently only supported for 0-order transforms


# Examples

```jldoctest
julia> q = QDHT{0, 1}(10, 128); A = exp.(-q.r.^2/2);
julia> onaxis(q*A, q) ≈ 1 # should be exp(0) = 1
true
```
