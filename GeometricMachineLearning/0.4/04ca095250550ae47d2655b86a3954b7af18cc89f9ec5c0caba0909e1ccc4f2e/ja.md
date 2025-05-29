```
rgrad(Y::StiefelManifold, ∇L::AbstractMatrix)
```

`Y`におけるStiefel多様体のリーマン勾配を`∇L`に基づいて計算します。

ここで$Y\in{}St(N,n)$および$\nabla{}L\in\mathbb{R}^{N\times{}n}$はユークリッド勾配です。

この関数は、標準的な計量に関するリーマン勾配を計算します: [`metric(::StiefelManifold, ::AbstractMatrix, ::AbstractMatrix)`](@ref)。

写像の正確な形は次の通りです：

$$
\mathtt{rgrad}(Y, \nabla{}L) \mapsto \nabla{}L - Y(\nabla{}L)^TY
$$

性質に注意してください：$Y^T\mathtt{rgrad}(Y, \nabla{}L)\in\mathcal{S}_\mathrm{skew}(n).$

# 例

```jldoctest
using GeometricMachineLearning

Y = StiefelManifold([1 0 ; 0 1 ; 0 0; 0 0])
Δ = [1 2; 3 4; 5 6; 7 8]
rgrad(Y, Δ)

# 出力

4×2 Matrix{Int64}:
 0  -1
 1   0
 5   6
 7   8
```
