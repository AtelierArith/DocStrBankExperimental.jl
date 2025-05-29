```
window_edge([T=Float64], size::NTuple; 
            offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

A multidimensional (separable) window with a sudden transition half way between the borders (`border_out`) to one (`border_in`). See `?window_linear` for more details on the arguments.

---

```
window_edge(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit,
                                  border_in=0.8, border_out=1.0)
```

This is a wrapper for  `window_edge(eltype(arr), size(arr), scaling=scaling, offset=offset, border_in=border_in, border_out=border_out)`.
