```
HAdaptError(; n=10)
```

Estimate the error of the interpolant by dividing the panel into two, computing interpolants on the subpanels, and computing the maximum error between interpolants at `n*p` equispaced points, where `p` is the number of points used to compute each interpolant.
