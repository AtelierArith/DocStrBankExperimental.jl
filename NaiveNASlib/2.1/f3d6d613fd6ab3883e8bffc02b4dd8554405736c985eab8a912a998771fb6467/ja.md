```
immutablevertex(computation, inputs::AbstractVertex...; traitdecoration=identity)
immutablevertex(vname::AbstractString, computation, inputs::AbstractVertex...; traitdecoration=identity)
immutablevertex(computation, vname::AbstractString, inputs::AbstractVertex...; traitdecoration=identity)
```

不変の計算タイプの頂点を返します。

`traitdecoration`を使用して、[`named`](@ref)、[`logged`](@ref)または[`validated`](@ref)などの他の特性を添付します。

# 例

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
