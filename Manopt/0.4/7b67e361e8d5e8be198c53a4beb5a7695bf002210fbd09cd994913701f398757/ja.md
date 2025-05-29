```
ManifoldDifferenceOfConvexObjective{E} <: AbstractManifoldCostObjective{E}
```

[`difference_of_convex_algorithm`](@ref)の目的を指定します。

目的 $f: \mathcal M → ℝ$ は次のように与えられます。

$$
    f(p) = g(p) - h(p)
$$

ここで、$g$ と $h$ はどちらも凸で、下半連続かつ適切です。さらに、$h$ のサブ微分 $∂h$ が必要です。

# フィールド

  * `cost`: 関数 `f(M,p)` としての $f(p) = g(p)-h(p)$ の実装。
  * `∂h!!`: $∂h: \mathcal M → T\mathcal M$ の決定論的バージョンであり、`∂h(M, p)` を呼び出すと `p` における $h$ のサブ勾配が返され、複数ある場合は決定論的な選択が返されます。

サブ微分は2つの可能なシグネチャで与えられることに注意してください。

  * `∂h(M,p)` は [`AllocatingEvaluation`](@ref) を行います。
  * `∂h!(M, X, p)` は `X` の代わりに [`InplaceEvaluation`](@ref) を行います。

```
