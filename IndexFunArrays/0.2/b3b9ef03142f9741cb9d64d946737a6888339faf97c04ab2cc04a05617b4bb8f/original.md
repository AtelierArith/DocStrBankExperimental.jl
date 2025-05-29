```
window_radial_linear([T=Float64], size::NTuple; 
            offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

A multidimensional radial window with a linear transition from zero at the borders (`border_out`) to one (`border_in`). Note that `border_in` and `border_out` need to be scalar values for `radial` type windows. The elypticity can be adjusted via the `scale` parameter. With the default offset and scale the borders are specified relative to the edge.

```jldoctest
julia> window_radial_linear((4,5),border_in=0.0)
4×5 IndexFunArray{Float64, 2, IndexFunArrays.var"#59#60"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}, Float64, Float64}}:
 0.0  0.0       0.0  0.0       0.0
 0.0  0.292893  0.5  0.292893  0.0
 0.0  0.5       1.0  0.5       0.0
 0.0  0.292893  0.5  0.292893  0.0
```

---

```
window_radial_linear(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit,
                     border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

This is a wrapper for  `window_radial_linear(eltype(arr), size(arr), scaling=scaling, offset=offset, border_in=border_in, border_out=border_out)`.
