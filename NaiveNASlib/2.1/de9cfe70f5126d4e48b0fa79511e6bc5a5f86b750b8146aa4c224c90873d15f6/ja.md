```
inputs(v)
```

与えられた頂点に入力される頂点の配列を返します。

# 例

```jldoctest
julia> using NaiveNASlib, NaiveNASlib.Extend

julia> inputs(CompVertex(identity, InputVertex(1)))
1-element Vector{AbstractVertex}:
 InputVertex(1)
```
