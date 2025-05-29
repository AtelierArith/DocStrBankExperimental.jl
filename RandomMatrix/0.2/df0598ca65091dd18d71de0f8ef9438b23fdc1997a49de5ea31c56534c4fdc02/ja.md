```julia
randMatrix(d::D, n::Int, m = n::Int; norm = false::Bool) where D<:S

randMatrix(n::Int, m = n::Int; norm = false::Bool)
```

  * `d` : エントリ分布
  * `n`,`m` : デフォルト `m = n` , 次元
  * `norm` : デフォルト `false`, `norm` が `true` に設定されている場合、行列は $\operatorname{min}(n,m)^{-1/2}$ で正規化されます。

# 例

標準ガウス分布からのエントリを持つ 2×2 のランダム行列を生成します。

```julia
randMatrix(2)

2×2 Matrix{Float64}:
 1.74043  -1.30317
 0.72765   0.639943
```

{1,2,3,...,10} から一様にエントリを持つ 3×2 のランダム行列を生成します。

```julia
randMatrix(1:10,3,2)

3×2 Matrix{Int64}:
  1  3
  6  4
 10  1
```

エントリが `Poisson(2)` の rvs である正規化された 2×2 のランダム行列を生成します。 `Poisson(2)` のために `Distributions` パッケージをインポートする必要があります。

```julia
using Distributions
randMatrix(Poisson(2),2,norm = true)

2×2 Matrix{Float64}:
 1.41421   0.0
 0.707107  1.41421
```
