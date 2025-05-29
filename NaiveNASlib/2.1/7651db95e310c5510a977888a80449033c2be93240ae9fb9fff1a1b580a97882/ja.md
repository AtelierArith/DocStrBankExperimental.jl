```
outputs(v)
```

与えられた頂点が入力としている頂点の配列を返します。

# 例

```jldoctest
julia> using NaiveNASlib

julia> iv = inputvertex("in", 3);

julia> cv = invariantvertex(identity, iv);

julia> outputs(iv)
1-element Vector{NaiveNASlib.AbstractVertex}:
 MutationVertex(CompVertex(identity, inputs=[in], outputs=[]), NaiveNASlib.SizeInvariant()) 
```
