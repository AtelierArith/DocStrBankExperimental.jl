```
AdaptiveRagularizationWithCubicsModelObjective
```

キュービックを用いた適応正則化のモデル

$$
m(X) = f(p) + ⟨\operatorname{grad} f(p), X ⟩_p + \frac{1}{2} ⟨\operatorname{Hess} f(p)[X], X⟩_p
       +  \frac{σ}{3} \lVert X \rVert^3,
$$

cf. Eq. (33) in [AgarwalBoumalBullinsCartis:2020](@cite)

# フィールド

  * `objective`: [`AbstractManifoldHessianObjective`](@ref) を提供する $f$、その勾配およびヘッセ行列
  * `σ`:         現在の（キュービック）正則化パラメータ

# コンストラクタ

```
AdaptiveRagularizationWithCubicsModelObjective(mho, σ=1.0)
```

[`AbstractManifoldHessianObjective`](@ref) `objective` またはそのような目的を含むデコレーターのいずれかを使用して。
