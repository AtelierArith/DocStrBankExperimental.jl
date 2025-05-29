```
struct SasakiRetraction <: AbstractRetractionMethod end
```

指数写像は、[MuralidharanFletcher:2012](@cite)で説明されているように、オイラー積分を介して計算された[`TangentBundle`](https://juliamanifolds.github.io/Manifolds.jl/stable/manifolds/vector_bundle.html#Manifolds.TangentBundle)上のものです。$\gamma : ℝ \to T\mathcal M$の方程式系は、$γ(1) = \exp_{p,X}(X_M, X_F)$および$γ(0)=(p, X)$を満たすように次のように表されます。

$$
\dot{γ}(t) = (\dot{p}(t), \dot{X}(t)) = (R(X(t), \dot{X}(t))\dot{p}(t), 0)
$$

ここで、$R$はリーマン曲率テンソルです（[`riemann_tensor`](@ref)を参照）。

# コンストラクタ

```
SasakiRetraction(L::Int)
```

このコンストラクタでは、`L`は積分ステップの数です。
