```
NaN, NaN64
```

A not-a-number value of type [`Float64`](@ref).

See also: [`isnan`](@ref), [`missing`](@ref), [`NaN32`](@ref), [`Inf`](@ref).

# Examples

```jldoctest
julia> 0/0
NaN

julia> Inf - Inf
NaN

julia> NaN == NaN, isequal(NaN, NaN), NaN === NaN
(false, true, true)
```
