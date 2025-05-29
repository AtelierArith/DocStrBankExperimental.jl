```
window_radial_blackman_harris([T=Float64], size::NTuple; 
                      offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

A multidimensional radial window with a Hamming transition according to Blackman/Harris between the borders (`border_out`) to one (`border_in`). Note that `border_in` and `border_out` need to be scalar values for `radial` type windows. The elypticity can be adjusted via the `scale` parameter. See `?window_radial_linear` for more details on the arguments.

---

```
window_radial_blackman_harris(arr::AbstractArray;
                              offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

This is a wrapper for  `window_radial_blackman_harris(eltype(arr), size(arr), scaling=scaling, offset=offset, border_in=border_in, border_out=border_out)`.
