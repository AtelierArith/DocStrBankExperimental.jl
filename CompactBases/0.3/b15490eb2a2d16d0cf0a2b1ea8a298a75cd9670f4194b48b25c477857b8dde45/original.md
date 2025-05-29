```
basis_overlap(A::BSplineOrRestricted, B::Union{BSplineOrRestricted,FEDVROrRestricted})
```

From a piecewise polynomial basis, i.e. B-splines or FEDVR, we can use Gaussian quadrature to compute the overlap matrix elements exactly. It is possible that we could derive better results, if we used the fact that FEDVR basis functions are orthogonal in the sense of the Gauss–Lobatto quadrature, but we leave that for later.
