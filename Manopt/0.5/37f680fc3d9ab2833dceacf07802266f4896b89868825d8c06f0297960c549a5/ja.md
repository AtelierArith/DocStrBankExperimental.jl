```
StopWhenCurvatureIsNegative <: StoppingCriterion
```

モデルの曲率が負であるかどうかをテストするファンクタ、$⟨δ_k, \operatorname{Hess} F(p)[δ_k]⟩_p ≦ 0$。この場合、モデルは厳密に凸ではなく、計算されたステップサイズはモデルの減少をもたらしません。

# フィールド

  * `at_iteration::Int`: 停止基準が最後に停止を示したイテレーションを示す整数で、ソルバーが開始する前（`0`）である可能性もあります。負の値は、まだそのようなことがなかったことを示します；
  * `value`: 内積の値を格納します。
  * `reason`: 停止基準が達成された場合の停止理由を格納します。詳細は[`get_reason`](@ref)を参照してください。

# コンストラクタ

```
StopWhenCurvatureIsNegative()
```

# 参照

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
