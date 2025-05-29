```
unsafe_get(x)
```

Return the value of `x` for [`Nullable`](@ref) `x`; return `x` for all other `x`.

This method does not check whether or not `x` is null before attempting to access the value of `x` for `x::Nullable` (hence "unsafe").

# Examples

```jldoctest
julia> x = Nullable(1)
Nullable{Int64}(1)

julia> unsafe_get(x)
1

julia> x = Nullable{String}()
Nullable{String}()

julia> unsafe_get(x)
ERROR: UndefRefError: access to undefined reference
Stacktrace:
 [1] unsafe_get(::Nullable{String}) at ./nullable.jl:152

julia> x = 1
1

julia> unsafe_get(x)
1
```
