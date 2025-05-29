```
doubledescription(h::HRepresentation)
```

Computes the V-representation of the polyhedron represented by `h` using the Double-Description algorithm [MRTT53, FP96]. It maintains a list of the points, rays and lines that are in the resulting representation and in the hyperplane corresponding to each halfspace and then add their intersection for each halfspace with [`Polyhedra.add_intersection!`](@ref). The resulting V-representation has no redundancy.

```
doubledescription(V::VRepresentation)
```

Computes the H-representation of the polyhedron represented by `v` using the Double-Description algorithm [MRTT53, FP96]. Currently, this fallbacks to lifting it to the V-representation of a cone by homogenization, interpreting it as the H-representation of the dual cone so that it can rely on `doubledescription(::HRepresentation)`.

[MRTT53] Motzkin, T. S., Raiffa, H., Thompson, G. L. and Thrall, R. M. The double description method *Contribution to the Theory of Games*, *Princeton University Press*, **1953**

[FP96] Fukuda, K. and Prodon, A. Double description method revisited *Combinatorics and computer science*, *Springer*, **1996**, 91-111
