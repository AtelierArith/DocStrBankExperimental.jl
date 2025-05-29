# Extended help

```
isconvextype(::Type{<:LazySet})
```

### Algorithm

The default implementation returns `false`. All set types that can determine convexity should override this behavior.

### Examples

A ball in the infinity norm is always convex:

```jldoctest convex_types
julia> isconvextype(BallInf)
true
```

The union (`UnionSet`) of two sets may in general be either convex or not. Since convexity cannot be decided by just using type information, `isconvextype` returns `false`.

```jldoctest convex_types
julia> isconvextype(UnionSet)
false
```

However, the type parameters of set operations allow to decide convexity in some cases by falling back to the convexity information of the argument types. Consider the lazy intersection. The intersection of two convex sets is always convex:

```jldoctest convex_types
julia> isconvextype(Intersection{Float64, BallInf{Float64}, BallInf{Float64}})
true
```
