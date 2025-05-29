```
immutablevertex(computation, inputs::AbstractVertex...; traitdecoration=identity)
immutablevertex(vname::AbstractString, computation, inputs::AbstractVertex...; traitdecoration=identity)
immutablevertex(computation, vname::AbstractString, inputs::AbstractVertex...; traitdecoration=identity)
```

Return an immutable computation type vertex.

Use `traitdecoration` to attach other traits, such as [`named`](@ref), [`logged`](@ref) or [`validated`](@ref).

# Examples

```jldoctest
julia> using NaiveNASlib

julia> v = immutablevertex(x -> x * [1 2 3; 4 5 6], inputvertex("input", 2));

julia> v([1 2])
1×3 Matrix{Int64}:
 9  12  15

julia> v = immutablevertex("v", x -> x * [1 2 3; 4 5 6], inputvertex("input", 2));

julia> name(v)
"v"

julia> v = immutablevertex("v", inputvertex("input", 2)) do x
           x * [1 2 3; 4 5 6]
       end;

julia> name(v)
"v"       
```
