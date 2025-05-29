```
struct GradedSpace{I<:Sector, D} <: ElementarySpace
    dims::D
    dual::Bool
end
```

A complex Euclidean space with a direct sum structure corresponding to labels in a set `I`, the objects of which have the structure of a monoid with respect to a monoidal product `⊗`. In practice, we restrict the label set to be a set of superselection sectors of type `I<:Sector`, e.g. the set of distinct irreps of a finite or compact group, or the isomorphism classes of simple objects of a unitary and pivotal (pre-)fusion category.

Here `dims` represents the degeneracy or multiplicity of every sector.

The data structure `D` of `dims` will depend on the result `Base.IteratorElsize(values(I))`; if the result is of type `HasLength` or `HasShape`, `dims` will be stored in a `NTuple{N,Int}` with `N = length(values(I))`. This requires that a sector `s::I` can be transformed into an index via `s == getindex(values(I), i)` and `i == findindex(values(I), s)`. If `Base.IteratorElsize(values(I))` results `IsInfinite()` or `SizeUnknown()`, a `SectorDict{I,Int}` is used to store the non-zero degeneracy dimensions with the corresponding sector as key. The parameter `D` is hidden from the user and should typically be of no concern.

The concrete type `GradedSpace{I,D}` with correct `D` can be obtained as `Vect[I]`, or if `I == Irrep[G]` for some `G<:Group`, as `Rep[G]`.
