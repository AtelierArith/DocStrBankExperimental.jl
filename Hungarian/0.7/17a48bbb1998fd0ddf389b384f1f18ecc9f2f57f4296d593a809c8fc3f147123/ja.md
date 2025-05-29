```
hungarian(costMat) -> (assignment, cost)
```

$$
N \times M
$$

行列 `costMat` で表される矩形割り当て問題の最適解を見つけます。最適な列インデックスと対応する最小コストを返します。

`costMat[n,m]` は、`n` 番目の作業者を `m` 番目の仕事に割り当てるための `cost` を示します。返り値 `assignment` のゼロ要素は、これらの作業者に割り当てられた仕事がないことを意味します。

行列の要素は `missing` に設定できます。この場合、対応するマッチングはアルゴリズムによって考慮されません。

# 例

```julia
julia> A = [ 24     1     8;
              5     7    14;
              6    13    20;
             12    19    21;
             18    25     2];

julia> assignment, cost = hungarian(A)
([2,1,0,0,3],8)

julia> assignment, cost = hungarian(A')
([2,1,5],8)

julia> using Missings

julia> costMat = [ missing  1   1
                      1     0   1
                      1     1   0 ]
3×3 Array{Union{Float64, Missings.Missing},2}:
missing  1.0  1.0
  1.0    0.0  1.0
  1.0    1.0  0.0

julia> hungarian(costMat)
([2, 1, 3], 2)
```
