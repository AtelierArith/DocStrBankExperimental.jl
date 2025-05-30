```
allequal(itr) -> Bool
```

Return `true` if all values from `itr` are equal when compared with [`isequal`](@ref).

See also: [`unique`](@ref), [`allunique`](@ref).

!!! compat "Julia 1.8"
    The `allequal` function requires at least Julia 1.8.


# Examples

```jldoctest
julia> allequal([])
true

julia> allequal([1])
true

julia> allequal([1, 1])
true

julia> allequal([1, 2])
false

julia> allequal(Dict(:a => 1, :b => 1))
false
```
