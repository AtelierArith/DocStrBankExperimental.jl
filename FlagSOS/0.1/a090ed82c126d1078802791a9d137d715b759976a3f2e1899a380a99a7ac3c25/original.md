```
generateAll(::Type{F}, maxVertices::Int, maxPredicates::Vector{Int}; withProperty = (F::T) -> true) where {F}
```

Generates all Flags of type `F` with up to `maxVertices` vertices and up to `maxPredicates` non-zero predicate values. 'maxPredicates' is a vector, for the case that there are multiple predicates. If a function `withProperty:F->{true, false}` is given, keeps adding edges to flags as long as the property holds.
