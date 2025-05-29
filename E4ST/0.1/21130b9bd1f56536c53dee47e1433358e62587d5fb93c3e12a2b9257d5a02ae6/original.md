```
get_type(sym::Symbol) -> type (preferred)

get_type(str::String) -> type
```

Returns the E4ST-related `type` corresponding to `str`.  See also `reload_types!`

# Examples:

```julia
julia> get_type("MyType")
ERROR: There has been no type MyType defined!
julia> struct MyType <: Policy end
julia> T = get_type("MyType")
MyType
julia> T()
MyType()
```
