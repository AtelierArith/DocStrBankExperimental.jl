```
BlockRange(axes::Tuple{AbstractUnitRange{Int}})
BlockRange(sizes::Vararg{Integer})
```

ブロックの直交範囲を表します。

`Block` と `BlockRange` の関係は、`CartesianIndex` と `CartesianIndices` の関係を模倣しています。

# 例

```jldoctest
julia> BlockRange(2:3, 3:4) |> collect
2×2 Matrix{Block{2, Int64}}:
 Block(2, 3)  Block(2, 4)
 Block(3, 3)  Block(3, 4)

julia> BlockRange(2, 2) |> collect # 要素の数、1から始まる
2×2 Matrix{Block{2, Int64}}:
 Block(1, 1)  Block(1, 2)
 Block(2, 1)  Block(2, 2)

julia> Block(1):Block(2)
BlockRange(1:2)
```
