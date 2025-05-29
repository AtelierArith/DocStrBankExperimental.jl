```
get_bipartition(tree::HybridNetwork, n::Int64)
```

系統樹の二分割形式を取得します。

# 引数

  * `tree`: 木を表すHybridNetworkオブジェクト。
  * `n`: 木のタクサの数。

# 出力

二分割形式で木を示すペアの`Vector`。

# 例

```jldoctest
julia> get_bipartition(readTopology("(4:4.249,(1:2.457,(2:2.064,3:2.064):0.393):1.793);"), 4)
6-element Vector{Any}:
 3 => 4.249
 0 => 2.457
 1 => 2.064
 2 => 2.064
 6 => 0.393
 3 => 1.793
```
