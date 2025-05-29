```
takestrict(xs, n::Int)
```

`take()`のように、`xs`の最初の`n`要素を最大で生成するイテレータですが、`xs`に`n`未満のアイテムが含まれている場合は例外をスローします。

```jldoctest
julia> collect(takestrict(1:2:11, 3))
3-element Vector{Int64}:
 1
 3
 5
```
