```
invariantvertex(computation, inputs::AbstractVertex...; traitdecoration=identity)
invariantvertex(vname::AbstractString, computation, inputs::AbstractVertex...; traitdecoration=identity)
invariantvertex(computation, vname::AbstractString, inputs::AbstractVertex...; traitdecoration=identity)
```

サイズ不変の可変計算タイプの頂点を返します。すなわち、`nin == nout`です。

`traitdecoration`を使用して、[`named`](@ref)、[`logged`](@ref) または [`validated`](@ref) などの他の特性を添付します。

# 例

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
