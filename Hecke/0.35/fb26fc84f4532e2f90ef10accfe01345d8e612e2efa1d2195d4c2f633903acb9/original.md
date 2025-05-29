```
torsion_quadratic_module(M::ZZLat, N::ZZLat; gens::Union{Nothing, Vector{<:Vector}} = nothing,
                                             snf::Bool = true,
                                             modulus::RationalUnion = QQFieldElem(0),
                                             modulus_qf::RationalUnion = QQFieldElem(0),
                                             check::Bool = true) -> TorQuadModule
```

Given a Z-lattice $M$ and a sublattice $N$ of $M$, return the torsion quadratic module $M/N$.

If `gens` is set, the images of `gens` will be used as the generators of the abelian group $M/N$.

If `snf` is `true`, the underlying abelian group will be in Smith normal form. Otherwise, the images of the basis of $M$ will be used as the generators.

One can decide on the modulus for the associated finite bilinear and quadratic forms by setting `modulus` and `modulus_qf` respectively to the desired values.
