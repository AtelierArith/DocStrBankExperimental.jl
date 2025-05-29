```
invariantvertex(computation, inputs::AbstractVertex...; traitdecoration=identity)
invariantvertex(vname::AbstractString, computation, inputs::AbstractVertex...; traitdecoration=identity)
invariantvertex(computation, vname::AbstractString, inputs::AbstractVertex...; traitdecoration=identity)
```

Return a mutable computation type vertex which is size invariant, i.e `nin == nout`.

Use `traitdecoration` to attach other traits, such as [`named`](@ref), [`logged`](@ref) or [`validated`](@ref).

# Examples

```jldoctest
julia> using NaiveNASlib

julia> v = invariantvertex(x -> 2 .* x, inputvertex("input", 2));

julia> nin(v)
1-element Vector{Int64}:
 2

julia> nout(v)
2

julia> v([1 2])
1×2 Matrix{Int64}:
 2  4

julia> v = invariantvertex("v", x -> 2 .* x, inputvertex("input", 2));

julia> name(v)
"v"

julia> v = invariantvertex("v", inputvertex("input", 2)) do x
           2 .* x
       end;

julia> name(v)
"v"    
```
