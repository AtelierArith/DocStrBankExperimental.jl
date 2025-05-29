```
absorbvertex(computation, inputs::AbstractVertex...; traitdecoration=identity)
absorbvertex(vname::AbstractString, computation, inputs::AbstractVertex...; traitdecoration=identity)
absorbvertex(computation, vname::AbstractString, inputs::AbstractVertex...; traitdecoration=identity)
```

Return a mutable computation type vertex which absorbs size changes. Typical example of this is a neural network layer wrapping a parameter array.

Use `traitdecoration` to attach other traits, such as [`named`](@ref), [`logged`](@ref) or [`validated`](@ref).

# Examples

```jldoctest
julia> using NaiveNASlib

julia> v = absorbvertex(x -> x * [1 2 3; 4 5 6], inputvertex("input", 2));

julia> v([1 2])
1×3 Matrix{Int64}:
 9  12  15

julia> v = absorbvertex("v", x -> x * [1 2 3; 4 5 6], inputvertex("input", 2));

julia> name(v)
"v"

julia> v = absorbvertex("v", inputvertex("input", 2)) do x
           x * [1 2 3; 4 5 6]
       end;

julia> name(v)
"v"       
```
