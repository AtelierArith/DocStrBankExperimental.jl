```
allunique(itr) -> Bool
```

Return `true` if all values from `itr` are distinct when compared with [`isequal`](@ref).

See also: [`unique`](@ref), [`issorted`](@ref), [`allequal`](@ref).

# Examples

```jldoctest
julia> allunique([1, 2, 3])
true

julia> allunique([1, 2, 1, 2])
false

julia> allunique(Real[1, 1.0, 2])
false

julia> allunique([NaN, 2.0, NaN, 4.0])
false
```
