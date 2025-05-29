```
window_linear([T=Float64], size::NTuple; 
            offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

A multidimensional (separable) window with a linear transition from zero at the borders (`border_out`) to one (`border_in`).

```jldoctest
julia> window_linear((8,9),border_in=0.0)
8×9 IndexFunArray{Float64, 2, IndexFunArrays.var"#34#35"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}, Float64, Float64}}:
 0.0  0.0     0.0    0.0     0.0   0.0     0.0    0.0     0.0
 0.0  0.0625  0.125  0.1875  0.25  0.1875  0.125  0.0625  0.0
 0.0  0.125   0.25   0.375   0.5   0.375   0.25   0.125   0.0
 0.0  0.1875  0.375  0.5625  0.75  0.5625  0.375  0.1875  0.0
 0.0  0.25    0.5    0.75    1.0   0.75    0.5    0.25    0.0
 0.0  0.1875  0.375  0.5625  0.75  0.5625  0.375  0.1875  0.0
 0.0  0.125   0.25   0.375   0.5   0.375   0.25   0.125   0.0
 0.0  0.0625  0.125  0.1875  0.25  0.1875  0.125  0.0625  0.0
```

---

```
window_linear(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit,
                                  border_in=0.8, border_out=1.0)
```

This is a wrapper for  `window_linear(eltype(arr), size(arr), scaling=scaling, offset=offset, border_in=border_in, border_out=border_out)`.
