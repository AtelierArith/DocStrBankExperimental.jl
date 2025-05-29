```
BitArraySpace(;dim)
```

ビット配列で区切られた探索空間を定義します。

# 例

```julia-repl
julia> space = BitArraySpace(4)
BitArraySpace(4)

julia> rand(space, 7)
7-element Vector{Vector{Bool}}:
 [0, 1, 1, 0]
 [0, 0, 0, 1]
 [1, 1, 1, 0]
 [0, 0, 0, 1]
 [0, 1, 0, 1]
 [1, 1, 1, 0]
 [1, 0, 0, 0]
```
