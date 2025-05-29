```
reduction(op, a; destination=MAIN [,init])
```

配列 `a` の値を操作 `op` と初期値 `init` に従って減少させ、結果を `a` と同じサイズの新しい配列のインデックス `destination` に格納します。

# 例

```jldoctest
julia> using PartitionedArrays

julia> a = [1,3,2,4]
4-element Vector{Int64}:
 1
 3
 2
 4

julia> reduction(+,a;init=0,destination=2)
4-element Vector{Int64}:
  0
 10
  0
  0
```
