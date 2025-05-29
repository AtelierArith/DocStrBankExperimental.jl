```
TrustRegionModelObjective{O<:AbstractManifoldHessianObjective} <: AbstractManifoldSubObjective{O}
```

信頼領域モデルの形式

$$
    m(X) = f(p) + ⟨\operatorname{grad} f(p), X⟩_p + \frac{1}{2} ⟨\operatorname{Hess} f(p)[X], X⟩_p
$$

# フィールド

  * `objective`: [`AbstractManifoldHessianObjective`](@ref) を提供する $f$、その勾配およびヘッセ行列

# コンストラクタ

```
TrustRegionModelObjective(objective)
```

[`AbstractManifoldHessianObjective`](@ref) `objective` またはそのような目的を含むデコレーターを持つもの
