```
show_bipartitions(n::Int64; start::Int64 = 0, stop::Int64=-1)
```

特定のインデックス間の二分割を、与えられたタクサの数に対して表示します。

# 引数

  * `n`: タクサの数
  * `start`（デフォルトは `0`）: 開始インデックス。
  * `stop`（デフォルトは `-1`）: 終了インデックス。

# 出力

`n` タクサの木の二分割を、`start` インデックスと `stop` インデックスの間で表示します。

# 例

```jldoctest
julia> show_bipartitions(4,stop = 4)
idx	partition
0	1 | 2 3 4 
1	2 | 1 3 4 
2	3 | 1 2 4 
3	4 | 1 2 3 
4	1 2 | 3 4 
```
