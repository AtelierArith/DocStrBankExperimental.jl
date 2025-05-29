```
struct BorderBasis{D,T,MT<:AbstractMatrix{T},B}
    dependence::BasisDependence{D,B}
    matrix::MT
end
```

This matrix with rows indexed by `standard` and columns indexed by `border` a `standard`-border basis of the ideal `border .- matrix' * standard` [LLR08, Section 2.5]. For solving this with a multiplication matrix solver, it is necessary for the basis `border` to be a superset of the set of *corners* of `standard` and it is sufficient for it to be the *border* of `standard`.

[LLR08] Lasserre, Jean Bernard and Laurent, Monique, and Rostalski, Philipp. *Semidefinite characterization and computation of zero-dimensional real radical ideals.* Foundations of Computational Mathematics 8 (2008): 607-647.
