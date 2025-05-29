```
kde(samples::AbstractVector; [boundary=(min,max), normalize="integral" or "max"])
kde(samples::AbstractMatrix; [boundary=[(min1,max1),(min2,max2)], normalize="integral" or "max", smooth_scale_2D])
```

Return a Kernel Density Estimate for a set of 1D or 2D samples. The return object is a function which can be evaluated anywhere to compute the PDF. If provided, `boundary` specifies a hard upper/lower bound for the 1 or 2 or parameters, `normalize` specifies whether to normalize the PDF to unit integral or unit maximum, and `smooth_scale_2D` specifies how much smoothing to do for the 2D case.

Based on Python [GetDist](https://getdist.readthedocs.io/en/latest/intro.html),  which must be installed.
