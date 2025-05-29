```
isdegenerate(surj::Surjection) -> Bool
```

A surjection is degenerate if two adjacent values are equal.

# Examples

```jldoctest
julia> isdegenerate(Surjection([1, 2, 1]))
false

julia> isdegenerate(Surjection([1, 1, 2]))
true
```
