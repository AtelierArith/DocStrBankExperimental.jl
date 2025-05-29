```
idx([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit)
```

See `rr2` for a description of all options.

Returns basically the `CartesianIndices` but as a tuple and accounting for optional `scale`, `offset` and data type. Note that `T` is enforced element-wise for the return tuple elements.

```jldoctest
julia> idx(Int, (3,3), offset=CtrCorner)
3×3 IndexFunArray{Tuple{Int64, Int64}, 2, IndexFunArrays.var"#39#40"{Int64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 (0, 0)  (0, 1)  (0, 2)
 (1, 0)  (1, 1)  (1, 2)
 (2, 0)  (2, 1)  (2, 2)

julia> idx(Int, (3,3), offset=(0,0))
3×3 IndexFunArray{Tuple{Int64, Int64}, 2, IndexFunArrays.var"#39#40"{Int64, Tuple{Int64, Int64}, Tuple{Int64, Int64}}}:
 (1, 1)  (1, 2)  (1, 3)
 (2, 1)  (2, 2)  (2, 3)
 (3, 1)  (3, 2)  (3, 3)

julia> idx(Float32, (3,3), offset=(0,0))
3×3 IndexFunArray{Tuple{Float32, Float32}, 2, IndexFunArrays.var"#39#40"{Float32, Tuple{Int64, Int64}, Tuple{Int64, Int64}}}:
 (1.0, 1.0)  (1.0, 2.0)  (1.0, 3.0)
 (2.0, 1.0)  (2.0, 2.0)  (2.0, 3.0)
 (3.0, 1.0)  (3.0, 2.0)  (3.0, 3.0)
```
