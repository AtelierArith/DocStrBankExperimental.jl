idx_max([T=Float64], size::NTuple{N, Int};         offset=CtrFT,         dims=ntuple(+, N),         scale=ScaUnit,         weight=1,         accumulator=sum)

returns the maximum of the absolute value of all index dimensions, after offset and scaling was applied. In combination with a comparison operation a box-shaped aperture is easily obtained. See below. See `rr2` for a description of all options.

```jldoctest
julia> idx_max((5,5)) .< 2
5×5 BitMatrix:
 0  0  0  0  0
 0  1  1  1  0
 0  1  1  1  0
 0  1  1  1  0
 0  0  0  0  0
```

---

```
idx_max(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

This is a wrapper for  `idx_max(eltype(arr), size(arr), scaling=scaling, offset=offset)`.
