```
integer_partitions(n [,m [; transpose=false [, count=false]]])
```

`default`                      : `n` の整数分割

`count`                        : `n` の整数分割の数

`transpose` = `false` (`m` > 0): 最大部分 `m` に制限された分割             = `true`  (`m` > 0): 最大長 `m` に制限された分割

定義:

正の整数 `n` の整数分割は、合計が `n` である非増加の正の整数の列 p1, p2,... pk です。列の要素は分割の部分と呼ばれます。

#### 例:

```
julia> integer_partitions(7)
15-element Vector{Vector{Int64}}:
 [1, 1, 1, 1, 1, 1, 1]
 [2, 2, 2, 1]
 [2, 2, 1, 1, 1]
 [2, 1, 1, 1, 1, 1]
 [3, 3, 1]
 [3, 2, 2]
 [3, 2, 1, 1]
 [3, 1, 1, 1, 1]
 [4, 3]
 [4, 2, 1]
 [4, 1, 1, 1]
 [5, 2]
 [5, 1, 1]
 [6, 1]
 [7]

julia> integer_partitions(7; count=true)
15

julia> integer_partitions(7, 4; count=true)
3

julia> integer_partitions(7, 4)
3-element Vector{Vector{Int64}}:
 [4, 3]
 [4, 2, 1]
 [4, 1, 1, 1]

julia> integer_partitions(7, 4; transpose=true)
3-element Vector{Vector{Int64}}:
 [2, 2, 2, 1]
 [3, 2, 1, 1]
 [4, 1, 1, 1]
```
