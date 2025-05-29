```julia
factorize(ABA)

```

ABA行列のLU因子分解行列をKLUを使用して評価します。

# 引数

  * `ABA::ABA_Matrix{Ax, L, Nothing} where {Ax, L <: NTuple{2, Dict}}`:       ABA行列のコンテナで、ABA.K == nothing（KのLU行列は評価されていない）
