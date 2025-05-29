```
emptyshim(ContainerType)
emptyshim(ContainerType, ElementType)
```

空の「シム」コンテナを作成し、要素を追加するときに `ContainerType` に拡張されます。デフォルトの `ElementType` は `Union{}` です。

# 例

```jldoctest
julia> using MicroCollections, BangBang

julia> @assert append!!(emptyshim(Vector), [0]) == [0]

julia> @assert merge!!(emptyshim(Dict), Dict(:a => 1)) == Dict(:a => 1)

julia> @assert union!!(emptyshim(Set), Set([0])) == Set([0])
```
