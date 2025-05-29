```
CombinationSpace(values; k)
CombinationSpace(k)
```

サイズ k の組み合わせ（重複を許す）によって定義される探索空間を定義します。

# 例

```julia-repl
julia> space = CombinationSpace(3)
CombinationSpace{UnitRange{Int64}}(1:3, 3)

julia> rand(space)
3-element Vector{Int64}:
 1
 1
 2

julia> rand(space,7)
7-element Vector{Vector{Int64}}:
 [1, 1, 1]
 [2, 1, 1]
 [2, 2, 1]
 [2, 3, 3]
 [1, 3, 1]
 [2, 1, 2]
 [2, 3, 1]

julia> rand(CombinationSpace([:apple, :orange, :onion, :garlic]))
4-element Vector{Symbol}:
 :apple
 :orange
 :orange
 :apple
```
