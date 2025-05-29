```julia
evaluateManifoldNaive1D!(ret, idx, pts, bw, x)
evaluateManifoldNaive1D!(ret, idx, pts, bw, x, loo)
evaluateManifoldNaive1D!(ret, idx, pts, bw, x, loo, diffop)

```

Evalute the KDE naively as equally weighted Gaussian kernels with common bandwidth. This function does, however, allow on-manifold evaluations.
