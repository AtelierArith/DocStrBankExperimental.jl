```
stirling2_partitions( n :: Int64, k :: Int64 ) :: Vector{Vector{Vector{Int64}}}
```

`n` 個のアイテムを `k` 個のラベルのないセットに分割するユニークなパーティションを列挙します。各パーティションは、各グループを指定する `k` 個のベクターを含むベクターです。

例：

```jldoctest
julia> stirling2_partitions( 4, 2 )
7-element Array{Array{Array{Int64,1},1},1}:
 [[1, 2, 3], [4]]
 [[3], [1, 2, 4]]
 [[1, 2], [3, 4]]
 [[1, 3], [2, 4]]
 [[2], [1, 3, 4]]
 [[2, 3], [1, 4]]
 [[1], [2, 3, 4]]
```

この再帰的アルゴリズムは [このブログ](https://devblogs.microsoft.com/oldnewthing/20140324-00/?p=1413) に触発されました。
