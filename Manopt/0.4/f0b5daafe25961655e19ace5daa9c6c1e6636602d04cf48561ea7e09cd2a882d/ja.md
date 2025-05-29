```
StopWhenCurvatureIsNegative <: StoppingCriterion
```

モデルの曲率が負であるかどうかをテストするファンクタ、$⟨δ_k, \operatorname{Hess}[F](\delta_k)⟩_p ≦ 0$。この場合、モデルは厳密に凸ではなく、計算されたステップサイズはモデルの減少をもたらしません。

# フィールド

  * `reason`: 停止基準が達成された場合の停止理由を格納します。詳細は[`get_reason`](@ref)を参照してください。

# コンストラクタ

```
StopWhenCurvatureIsNegative()
```

# 参照

[`truncated_conjugate_gradient_descent`](@ref)、[`trust_regions`](@ref)
