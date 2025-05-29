```
polar(S::AbstractMatrix) -> Polar
polar(S::Symplectic) -> Polar
```

シンプレクティック行列 `S` の極分解を計算し、`Polar` オブジェクトを返します。

`O` と `P` は、因子分解 `F` から `F.O` と `F.P` を介して取得でき、`S = O * P` となります。シンプレクティック極分解の場合、`O` は直交シンプレクティック行列であり、`P` は正定値対称シンプレクティック行列です。

分解を繰り返すことで、成分 `O` と `P` を得ることができます。

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
O因子:
2×2 Matrix{Float64}:
  0.894427  0.447214
 -0.447214  0.894427
P因子:
2×2 Matrix{Float64}:
 0.894427  0.447214
 0.447214  1.34164

julia> isapprox(F.O * F.P, S)
true

julia> O, P = F; # 繰り返しによる分解

julia> O == F.O && P == F.P
true
```
