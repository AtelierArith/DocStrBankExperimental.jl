```
isabstracttype(T)
```

Determine whether type `T` was declared as an abstract type (i.e. using the `abstract type` syntax).

# Examples

```jldoctest
julia> isabstracttype(AbstractArray)
true

julia> isabstracttype(Vector)
false
```
