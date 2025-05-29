```
Cut(n::Integer)
```

は `n` での [カット](https://en.wikipedia.org/wiki/Cut_(cards)) を表し、`n` までの要素がコレクションの底または端に移動し、残りの要素が先頭にシフトします。

このシャッフルタイプには、インプレースの [`shuffle!`](@ref) や [`nshuffle!`](@ref) は存在しません。

# 例

```jldoctest
julia> shuffle([1, 2, 3, 4, 5, 6, 7], Cut(3))
7-element Array{Int64,1}:
 4
 5
 6
 7
 1
 2
 3
```
