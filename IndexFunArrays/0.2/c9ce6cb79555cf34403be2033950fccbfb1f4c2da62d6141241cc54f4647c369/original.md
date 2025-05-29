```
window_radial_gaussian([T=Float64], size::NTuple; 
                      offset=CtrFT, scale=ScaFTEdge, border_in=0.8, border_out=1.0, dims=ntuple(+, N))
```

A multidimensional radial window with a Gaussian transition between the borders (`border_out`) to one (`border_in`). By default the standard deviation `sigma` of the Gaussian is adjusted such that the `2 sigma` level is reached at `border_out`. However, this window is not clipped at the outer border, thus allowing the sigma to be adjusted by placing `border_out` closer to `border_in`. Note that `border_in` and `border_out` are scalar values for `radial` type windows. The elypticity can be adjusted via the `scale` parameter. See `?window_radial_linear` for more details on the arguments.

---

window*radial*gaussian(arr::AbstractArray;                                   offset=CtrFT, scale=ScaFTEdge, border*in=0.8, border*out=1.0, dims=ntuple(+, N)) This is a wrapper for  `window_radial_gaussian(eltype(arr), size(arr), scaling=scaling, offset=offset, border_in=border_in, border_out=border_out)`.
