```
dither!([out,] img, alg::AbstractDither, ncolors; maxiter, tol, kwargs...)
```

Dither image `img` using algorithm `alg`. A color palette of size `ncolors` is computed by ColorQuantization.jl's `KMeansQuantization`, which applies K-means clustering.
