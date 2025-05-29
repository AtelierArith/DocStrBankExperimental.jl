```
absorbvertex(computation, inputs::AbstractVertex...; traitdecoration=identity)
absorbvertex(vname::AbstractString, computation, inputs::AbstractVertex...; traitdecoration=identity)
absorbvertex(computation, vname::AbstractString, inputs::AbstractVertex...; traitdecoration=identity)
```

サイズ変更を吸収する可変計算タイプの頂点を返します。これの典型的な例は、パラメータ配列をラップするニューラルネットワーク層です。

`traitdecoration`を使用して、[`named`](@ref)、[`logged`](@ref)または[`validated`](@ref)などの他の特性を添付します。

# 例

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
