```
struct BasisDependence{D,B<:MB.AbstractPolynomialBasis}
    basis::B
    dependence::Vector{D}
end
```

The dependence between the elements of a basis.

!!! tip
    If the number of variables is 2 or 3, it can be visualized with Plots.jl.

