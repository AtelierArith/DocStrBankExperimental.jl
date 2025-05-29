Abstract base type for a category.

The objects and morphisms in the category have Julia types `Ob` and `Hom`, respectively. Note that these types do *not* necessarily form an `@instance` of the theory of categories, as they may not meaningfully form a category outside the context of this object. For example, a finite category regarded as a reflexive graph with a composition operation might have type `Cat{Int,Int}`, where the objects and morphisms are numerical identifiers for vertices and edges in the graph.

The basic operations available in any category are: [`dom`](@ref), [`codom`](@ref), [`id`](@ref), [`compose`](@ref).
