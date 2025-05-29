```
remapbags(b::AbstractBags, idcs::VecOrRange{<:Integer}) -> (rb, I)
```

`b`のインデックス`idcs`に対応するバッグのサブセットを選択し、インスタンスインデックスを適切に再マッピングします。新しいバッグ`rb`と再マッピングされたインスタンスの`Vector` `I`を返します。

# 例

```jldoctest
julia> remapbags(AlignedBags([1:1, 2:3, 4:5]), [1, 3])
(AlignedBags{Int64}(UnitRange{Int64}[1:1, 2:3]), [1, 4, 5])

julia> remapbags(ScatteredBags([[1,3], [2], Int[]]), [2])
(ScatteredBags{Int64}([[1]]), [2])
```
