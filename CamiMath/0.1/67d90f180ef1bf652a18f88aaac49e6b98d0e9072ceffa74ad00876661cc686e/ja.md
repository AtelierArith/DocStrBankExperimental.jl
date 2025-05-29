```
canonical_partitions(n::Int, [m=0 , [sense=rev [; header=true]]])
```

最大サイズ `m` の部分における `n` の標準的な分割（`m` = 0 は任意のサイズ）

`sense` : 通常 ([`reg`](@ref)) または 逆 ([`rev`](@ref))     `header` : 単位分割が出力に含まれる

#### 例:

```
julia> canonical_partitions(6, 0, reg; header=true)
6-element Vector{Vector{Int64}}:
 [6]
 [5, 1]
 [4, 2]
 [3, 3]
 [2, 2, 2]
 [1, 1, 1, 1, 1, 1]

julia> canonical_partitions(6; header=true)
6-element Vector{Vector{Int64}}:
 [1, 1, 1, 1, 1, 1]
 [2, 2, 2]
 [3, 3]
 [4, 2]
 [5, 1]
 [6]

julia> canonical_partitions(6)
6-element Vector{Vector{Int64}}:
 [1, 1, 1, 1, 1, 1]
 [2, 2, 2]
 [3, 3]
 [4, 2]
 [5, 1]
 [6]

julia> o = canonical_partitions(9, 2); println(o)
[2, 2, 2, 2, 1]

julia> o = canonical_partitions(9, 3); println(o)
[3, 3, 3]
```
