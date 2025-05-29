```
NLADefault()
```

`NLADefault`はデフォルトの非線形アルゴリズムオプションを表します。使用すると、入力配列は変更されません。

# 例

```jldoctest
julia> nlat = NLADefault()
NLADefault()

julia> x_old = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
10-element Vector{Int64}:
 0
 1
 2
 3
 4
 5
 6
 7
 8
 9

julia> n_new = nlat(x_old)
10-element Vector{Int64}:
 0
 1
 2
 3
 4
 5
 6
 7
 8
 9

julia> mat_old = [1 2 3;
                  4 5 6;
                  7 8 9;
                  10 11 12;
                  13 14 15;
                  16 17 18;
                  19 20 21]
7×3 Matrix{Int64}:
  1   2   3
  4   5   6
  7   8   9
 10  11  12
 13  14  15
 16  17  18
 19  20  21

julia> mat_new = nlat(mat_old)
7×3 Matrix{Int64}:
  1   2   3
  4   5   6
  7   8   9
 10  11  12
 13  14  15
 16  17  18
 19  20  21
```
