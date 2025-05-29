```
overapproximate(P::SimpleSparsePolynomialZonotope, ::Type{<:Zonotope},
                dom::IntervalBox)
```

Overapproximate a simple sparse polynomial zonotope over the parameter domain `dom` with a zonotope.

### Input

  * `P`         – simple sparse polynomial zonotope
  * `Zonotope`  – target set type
  * `dom`       – parameter domain, which should be a subset of `[-1, 1]^q`,                where `q = nparams(P)`

### Output

A zonotope.
