```
rgrad(Y::GrassmannManifold, ∇L::AbstractMatrix)
```

Grassmann多様体における点`Y`でのリーマン勾配を`∇L`に基づいて計算します。

ここで$Y$は$\mathrm{span}(Y)\in{}Gr(n, N)$の表現であり、$\nabla{}L\in\mathbb{R}^{N\times{}n}$はユークリッド勾配です。

この勾配は、$Y$によって張られる空間に直交する性質を持っています。

マッピングの正確な形は次の通りです：

$$
\mathtt{rgrad}(Y, \nabla{}L) \mapsto \nabla{}L - YY^T\nabla{}L.
$$

$$
Y^T\mathrm{rgrad}(Y, \nabla{}L) = \mathbb{O}
$$

という性質にも注意してください。

また、[`rgrad(::StiefelManifold, ::AbstractMatrix)`](@ref)も参照してください。

# 例

```jldoctest
using GeometricMachineLearning

Y = GrassmannManifold([1 0 ; 0 1 ; 0 0; 0 0])
Δ = [1 2; 3 4; 5 6; 7 8]
rgrad(Y, Δ)

# 出力

4×2 Matrix{Int64}:
 0  0
 0  0
 5  6
 7  8
```
