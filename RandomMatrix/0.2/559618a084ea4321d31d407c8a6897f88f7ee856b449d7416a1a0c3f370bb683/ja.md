```julia
randToeplitz(d, n;  norm, hermitian)  
```

  * `d` : エントリ分布
  * `n` : 次元
  * `norm` : デフォルト `false`;  `norm` が `true` に設定されている場合、行列は $n^{-1/2}$ で正規化されます。
  * `hermitian`: デフォルト `true`; `true` の場合、行列はエルミートになります

# 例

エントリが標準正規分布の $4 \times 4$ のランダムエルミートToeplitz行列を生成します。

```julia
randToeplitz(4)

4×4 Matrix{Float64}:
  1.10207   -0.47292   -0.745498   1.06809
 -0.47292    1.10207   -0.47292   -0.745498
 -0.745498  -0.47292    1.10207   -0.47292
  1.06809   -0.745498  -0.47292    1.10207
```

エントリが `Exponential(1)` の $4 \times 4$ の正規化されたランダムToeplitz行列を生成します。

```julia
using Distributions
randToeplitz(Exponential(1),4, norm = true, hermitian = false)

4×4 Matrix{Float64}:
 0.667888  0.260045  1.48812   0.477305
 1.50374   0.667888  0.260045  1.48812
 1.1475    1.50374   0.667888  0.260045
 0.363966  1.1475    1.50374   0.667888
```
