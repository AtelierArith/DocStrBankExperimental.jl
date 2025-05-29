必ずしも最小の生成集合である必要はない生成集合から、最小の生成集合を返します。

入力は実相のみを含む必要があります。

```jldoctest
julia> minimal_generating_set(S"__ XZ ZX YY")
+ XZ
+ ZX
```
