Golden section search.

Given a function f with a single local minimum in the interval [a,b], gss returns a subset interval [c,d] that contains the minimum with d-c <= tol.

# Examples

```jldoctest
julia> f(x) = -(x-2)^2
f (generic function with 1 method)

julia> m = golden_section_maximize(f, 1, 5, identity, 1e-10)
2.0000000000051843
```

From: https://en.wikipedia.org/wiki/Golden-section_search
