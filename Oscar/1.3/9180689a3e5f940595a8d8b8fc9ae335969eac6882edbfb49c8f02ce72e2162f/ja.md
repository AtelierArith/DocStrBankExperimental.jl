```
SubPcGroupElem
```

多項群の部分群の要素。

要素は、完全多項群の要素と同じ方法で表示されます。詳細は[`PcGroupElem`](@ref)を参照してください。

# 例

```jldoctest
julia> G = abelian_group(SubPcGroup, [4, 2]);

julia> G[1], G[2]
(f1, f3)

julia> G[2]*G[1]
f1*f3
```
