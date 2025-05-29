```
GpBasisFnsζ(gpwζ::Float64, ζ::Float64, kv::KnotVector)
```

1-D basis functions $N(ζ)$ at the provided quadrature point `ζ` with weight `gpwζ`.

The B-spline values and derivatives are determined with [`get_bspline_ders`](@ref) and stored here. The struct contains four fields:

  * `w`   –> Gauss point weight, passed in as `gpw`
  * `N`   –> (`poly`+1)×1 vector of nonzero basis functions $N(ζ)$
  * `dN`  –> (`poly`+1)×1 vector of nonzero first derivatives $N'(ζ)$
  * `ddN` –> (`poly`+1)×1 vector of nonzero second derivatives $N''(ζ)$
