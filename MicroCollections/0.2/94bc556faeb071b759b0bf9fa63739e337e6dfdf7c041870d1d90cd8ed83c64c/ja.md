```
singletonshim(ContainerType, x)
```

要素 `x` を持つ「シム」コンテナを作成し、要素を追加する際に `ContainerType` に広げます。

# 例

```jldoctest
julia> using MicroCollections, BangBang

julia> @assert push!!(singletonshim(BitVector, false), true)::BitArray == [false, true]
```
