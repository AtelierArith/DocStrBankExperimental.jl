```
hermitian_structure(L::ZZLat, f::QQMatrix; check::Bool = true
                                           ambient_representation::Bool = true)
                                                                 -> HermLat
```

Given a $\mathbb{Z}$-lattice `L` together with an isometry `f` with irreducible minimal polynomial, return the associated hermitian structure on `(L, f)`.

Note that `f` must be of infinite order or of order at least 3. In which case, the rank of the lattice `L` should be divisible by the degree of the minimal polynomial of `f`.

If `L` is not of full rank, then the associated map of change of scalars is defined on the rational span of `L` (see [`rational_span(::ZZLat)`](@ref)), since only the action on the rational span of the lattice matters for the trace equivalence. If `L` is of full rank, we use its ambient space as rational span since both are isometric (see [`ambient_space(::ZZLat)`](@ref))

If `ambient_representation` is set to true, then the isometry `f` is seen as an isometry of the ambient space of `L`. If `check == true`, then the function checks whether the minimal polynomial of the action of `f` on the rational span of `L` is irreducible.
