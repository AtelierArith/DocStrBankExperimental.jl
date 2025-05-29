```
struct PSDMatrixInnerCone{MCT <: MOI.AbstractVectorSet} <: PolyJuMP.PolynomialSet
end
```

Inner approximation of the cone of polynomial matrices `P(x)` that are positive semidefinite for any `x` defined by the set of $n \times n$ polynomial matrices such that the polynomial $y^\top P(x) y$ belongs to `NonnegPolyInnerCone{MCT}` where `y` is a vector of $n$ auxiliary polynomial variables.
