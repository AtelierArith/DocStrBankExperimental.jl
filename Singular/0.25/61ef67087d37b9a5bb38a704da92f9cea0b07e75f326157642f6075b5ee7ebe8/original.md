```
divrem(I::smodule{S}, G::smodule{S}; complete_reduction::Bool = false) where S <: SPolyUnion
```

Computes a division with remainder of the generators of `I` by the generators of `G`. Returns a tuple (Quo, Rem, U) where `Matrix(I)*Matrix(U) = Matrix(G)*Matrix(Quo) + Matrix(Rem)` and `Rem = normalform(I, G)`. `U` is a diagonal matrix of units differing from the identity matrix only for local ring orderings.
