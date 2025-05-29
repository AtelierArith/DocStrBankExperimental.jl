```
axes1d(size::NTuple{N, Int}; offset=CtrFT, scale=ScaUnit, dims=ntuple(+, N), accumulator=sum, weight=1) where {N}
returns a tuple of axes, all oriented along x.
This is very useful for plotting (see example below). 
The optional argument `keepdims` can be used to obtain oriented single-dimensional vectors
which can be used in analogy to `meshgrid` operations but supporting broadcasting and generator performance.
See `rr2` for a description of other options.
```

```jldoctest
julia> using Plots, IndexFunArrays

julia> sz = (200,100);

julia> heatmap(axes1d(sz)..., rr(sz)')

julia> x,y = axes1d((10,11), keepdims=true)
"hi" = "hi"
Base.Generator{Tuple{Int64, Int64}, IndexFunArrays.var"#675#677"{Float64, Tuple{Int64, Int64}, Tuple{Int64, Int64}, Tuple{Int64, Int64}}}(IndexFunArrays.var"#675#677"{Float64, Tuple{Int64, Int64}, Tuple{Int64, Int64}, Tuple{Int64, Int64}}((6, 6), (1, 1), (10, 11)), (1, 2))

julia> size(y)
(1, 11)
```

---

axes1d(arr::AbstractArray{T, N}; offset=CtrFT, scale=ScaUnit, dims=ntuple(+, N), accumulator=sum, weight=1) where {N}

This is a wrapper for  `axes1d(size(arr); offset=CtrFT, scale=ScaUnit, dims=ntuple(+, N), accumulator=sum, weight=1) where {N}`
