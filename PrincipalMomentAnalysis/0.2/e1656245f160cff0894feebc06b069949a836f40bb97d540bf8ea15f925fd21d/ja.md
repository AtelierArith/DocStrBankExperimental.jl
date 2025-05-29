```
groupsimplices(groupby::AbstractVector)
```

同じ値を持つ要素を接続するSimplexGraphを作成します。

# 例

```
julia> sg = groupsimplices(["A","A","B","C","B"]);

julia> sg.G
5×3 BitArray{2}:
 1  0  0
 1  0  0
 0  1  0
 0  0  1
 0  1  0

julia> sg.w
3-element Array{Int64,1}:
 2
 2
 1
```
