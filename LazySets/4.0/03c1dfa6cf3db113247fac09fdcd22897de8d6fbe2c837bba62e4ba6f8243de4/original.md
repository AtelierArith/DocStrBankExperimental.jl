# Extended help

```
isoperation(X::LazySet)
```

### Algorithm

The default implementation checks whether the set type of the input is an operation type using [`isoperationtype(::Type{<:LazySet})`](@ref).

### Examples

```jldoctest
julia> B = BallInf([0.0, 0.0], 1.0);

julia> isoperation(B)
false

julia> isoperation(B ⊕ B)
true
```
