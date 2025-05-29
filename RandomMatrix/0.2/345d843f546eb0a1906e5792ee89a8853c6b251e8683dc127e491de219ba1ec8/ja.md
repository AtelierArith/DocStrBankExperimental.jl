```julia
randDiagonal(d, n) 

randDiagonal(n) 
```

  * `d` : デフォルト `Normal(0，1)`, エントリ分布
  * `n` : 次元

# 例

`Normal(0,1)` からの非ゼロ要素を持つ 3×3 対角行列を生成します。

```julia
randDiagonal(3)

3×3 Diagonal{Float64, Vector{Float64}}:
 0.440359   ⋅         ⋅
  ⋅        1.94832    ⋅
  ⋅         ⋅       -0.52536
```

`Poisson(2)` からの非ゼロ要素を持つ 5×5 対角行列を生成します。

```julia
randDiagonal(Poisson(2),5)

5×5 Diagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅  ⋅
 ⋅  0  ⋅  ⋅  ⋅
 ⋅  ⋅  0  ⋅  ⋅
 ⋅  ⋅  ⋅  3  ⋅
 ⋅  ⋅  ⋅  ⋅  3
```
