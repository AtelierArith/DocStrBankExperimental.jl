```
Polar <: Factorization
```

シンプレクティック行列 `S` の極分解の行列因子化タイプです。これは、対応する行列因子化関数 [`polar(_)`](@ref) の戻り値の型です。

`F::Polar` が因子化オブジェクトである場合、`O` と `P` は `F.O` と `F.P` を介して取得でき、`S = O * P` となります。

分解を繰り返すことで、成分 `O` と `P` が得られます。

# 例

```jldoctest
julia> S = [1. 1.; 0. 1.]
2×2 Matrix{Float64}:
 1.0  1.0
 0.0  1.0

julia> issymplectic(BlockForm(1), S)
true

julia> F = polar(S)
Polar{Float64, Matrix{Float64}, Matrix{Float64}}
O 因子:
2×2 Matrix{Float64}:
  0.894427  0.447214
 -0.447214  0.894427
P 因子:
2×2 Matrix{Float64}:
 0.894427  0.447214
 0.447214  1.34164

julia> isapprox(F.O * F.P, S)
true

julia> O, P = F; # 繰り返しによる分解

julia> O == F.O && P == F.P
true
```
