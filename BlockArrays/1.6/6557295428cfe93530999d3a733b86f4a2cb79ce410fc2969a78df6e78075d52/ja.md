```
blockaxes(A::AbstractArray, d::Int)
```

配列 `A` の次元 `d` に沿ったブロックインデックスの有効範囲を返します。

# 例

```jldoctest
julia> A = BlockArray([1,2,3], [2,1])
2-blocked 3-element BlockVector{Int64}:
 1
 2
 ─
 3

julia> blockaxes(A,1)
BlockRange(Base.OneTo(2))

julia> blockaxes(A,1) |> collect
2-element Vector{Block{1, Int64}}:
 Block(1)
 Block(2)
```
