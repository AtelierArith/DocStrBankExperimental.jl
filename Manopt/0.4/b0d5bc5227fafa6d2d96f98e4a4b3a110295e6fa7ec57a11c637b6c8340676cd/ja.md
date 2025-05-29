```
ManifoldDifferenceOfConvexProximalObjective{E} <: Problem
```

目的関数 [`difference_of_convex_proximal_point`](@ref) アルゴリズムを指定します。問題は次の形です。

$$
    \operatorname*{argmin}_{p∈\mathcal M} g(p) - h(p)
$$

ここで、$g$ と $h$ はどちらも凸で、下半連続かつ適切です。

# フィールド

  * `cost`:     （`nothing`）$f(p) = g(p)-h(p)$ の実装（オプション）
  * `gradient`: コストの勾配
  * `grad_h!!`: 関数 $\operatorname{grad}h: \mathcal M → T\mathcal M$、

両方の勾配は、割り当てまたはインプレースの2つの可能なシグネチャで与えられる場合があります。

# コンストラクタ

```
ManifoldDifferenceOfConvexProximalObjective(gradh; cost=nothing, gradient=nothing)
```

コストや勾配はアルゴリズムに必須ではなく、最終的なデバッグや停止基準のために必要です。
