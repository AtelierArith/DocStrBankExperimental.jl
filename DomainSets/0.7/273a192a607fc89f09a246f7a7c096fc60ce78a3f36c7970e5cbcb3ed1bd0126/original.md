```
ProductDomain(domains...)
ProductDomain{T}(domains...)
```

Return a concrete subtype of `ProductDomain` which agrees mathematically with the cartesian product of the given domains.

The concrete subtype being returned depends on `T`. If `T` is provided, it will be the eltype of the product domain. If `T` is not provided, a suitable choice is deduced from the arguments.

See also: [`VcatDomain`](@ref), [`VectorProductDomain`](@ref), [`TupleProductDomain`](@ref), [`Rectangle(a,b)`](@ref).
