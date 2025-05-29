```
empirical_interpolation(a::Projection) -> (AbstractVector,AbstractMatrix)
```

Computes the EIM of `a`. The outputs are:

  * a vector of integers `i`, corresponding to a list of interpolation row indices
  * a matrix `Φi = view(Φ,i)`, where `Φ = get_basis(a)`. This quantity represents the restricted basis on the set of interpolation rows `i`
