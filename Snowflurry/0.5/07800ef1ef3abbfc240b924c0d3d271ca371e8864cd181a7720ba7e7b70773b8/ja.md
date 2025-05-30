```
get_adjacency_list(connectivity::AbstractConnectivity)::Dict{Int,Vector{Int}}
```

`AbstractConnectivity`型のオブジェクトを与えると、`get_adjacency_list`は各キーがキュービットインデックスである`Dict`を返します。辞書の各値は、接続性においてキーのキュービットに隣接するすべてのキュービットをリストした`Vector`です。`connectivity.excluded_positions`の位置は、キーや値として含まれません。

# 例

```jldoctest
julia> connectivity = LineConnectivity(6)
LineConnectivity{6}
1──2──3──4──5──6


julia> get_adjacency_list(connectivity)
Dict{Int64, Vector{Int64}} with 6 entries:
  5 => [4, 6]
  4 => [3, 5]
  6 => [5]
  2 => [1, 3]
  3 => [2, 4]
  1 => [2]

julia> connectivity = LatticeConnectivity(3, 4)
LatticeConnectivity{3,4}
        1 
        | 
  9 ──  5 ──  2 
        |     | 
       10 ──  6 ──  3 
              |     | 
             11 ──  7 ──  4 
                    |     | 
                   12 ──  8 
  
julia> get_adjacency_list(connectivity)
Dict{Int64, Vector{Int64}} with 12 entries:
  5  => [1, 10, 9, 2]
  12 => [7, 8]
  8  => [4, 12]
  1  => [5]
  6  => [2, 11, 10, 3]
  11 => [6, 7]
  9  => [5]
  3  => [7, 6]
  7  => [3, 12, 11, 4]
  4  => [8, 7]
  2  => [6, 5]
  10 => [5, 6]

```

!!! note
    `get_adjacency_list`関数は`AllToAllConnectivity`には使用できません。このタイプの接続性は、キュービットの数に上限を設けず、すべてのキュービットが定義上互いに接続されるためです。したがって、隣接するキュービットの有限リストを構築することはできません。

