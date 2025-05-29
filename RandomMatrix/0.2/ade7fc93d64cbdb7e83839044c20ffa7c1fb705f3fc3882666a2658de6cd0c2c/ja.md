```julia
randTriangular(d , n ;  diag , Diag, upper ) 

randTriangular(n;diag, upper)
```

  * `d` : エントリ分布
  * `n` : 次元
  * `diag` : デフォルト `diag = d`、対角エントリ分布
  * `Diag` : デフォルト `Diag = true`、`true` は対角を含む、`false` は対角エントリを 0 にする
  * `upper` : デフォルト `upper = true`、`true` は上三角行列を生成、`false` は下三角行列を生成

# 例

エントリが標準正規分布の上三角行列を生成

```julia
randTriangular(3)

3×3 UpperTriangular{Float64, Matrix{Float64}}:
 -0.572757  -0.459518   -1.60622
   ⋅         0.0216834  -0.416529
   ⋅          ⋅         -1.00807
```

非ゼロエントリが $\{1,2,3\}$ から一様に選ばれる 3×3 の厳密な下三角行列を生成

```julia
randTriangular(1:3,3,upper=false,Diag=false)

3×3 LowerTriangular{Int64, Transpose{Int64, Matrix{Int64}}}: 
 0  ⋅  ⋅
 3  0  ⋅
 3  2  0
```
