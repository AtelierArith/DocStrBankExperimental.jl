```
RangeNode
```

整数の区間を[UnitRange](@ref)として表現した、拡張されたバランスの取れた二分[区間木](https://en.wikipedia.org/wiki/Interval_tree#Augmented_tree)です。

```jldoctest julia> rn = RangeNode([0:0, 3:40, 10:14, 20:35, 29:98]); # Wikipediaページからの例

julia> intersect(40:59, rn) 2-element Vector{UnitRange{Int64}}:  40:40  40:59 ````
