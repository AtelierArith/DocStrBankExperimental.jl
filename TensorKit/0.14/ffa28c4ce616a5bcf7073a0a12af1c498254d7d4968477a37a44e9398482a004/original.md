```
struct ProductSpace{S<:ElementarySpace, N} <: CompositeSpace{S}
```

A `ProductSpace` is a tensor product space of `N` vector spaces of type `S<:ElementarySpace`. Only tensor products between [`ElementarySpace`](@ref) objects of the same type are allowed.
