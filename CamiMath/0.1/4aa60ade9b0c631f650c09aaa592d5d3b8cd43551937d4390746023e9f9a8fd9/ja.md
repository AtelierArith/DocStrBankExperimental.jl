```
pascal_triangle(n::Integer [; arr=false [, msg=true]])
```

パスカルの三角形の行 `n`、$r_n = [\binom{n}{1},\cdots\ \binom{n}{n}]$

  * `arr` : 完全なパスカルの三角形を出力
  * `msg` : 整数オーバーフロー保護 (IOP) - 有効化時の警告

（`n > 10000` の場合）

#### 例:

```
julia> [pascal_triangle(n) for n=0:5]
6-element Vector{Vector{Int64}}:
 [1]
 [1, 1]
 [1, 2, 1]
 [1, 3, 3, 1]
 [1, 4, 6, 4, 1]
 [1, 5, 10, 10, 5, 1]

julia> pascal_triangle(5; arr=true)
5-element Vector{Vector{Int64}}:
 [1, 1]
 [1, 2, 1]
 [1, 3, 3, 1]
 [1, 4, 6, 4, 1]
 [1, 5, 10, 10, 5, 1]
```
