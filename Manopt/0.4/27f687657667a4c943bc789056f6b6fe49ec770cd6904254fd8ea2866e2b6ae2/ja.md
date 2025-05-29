```
StopWhenModelIncreased <: StoppingCriterion
```

モデル値の曲率が増加したかどうかをテストするためのファンクタ。

# フィールド

  * `reason`: 停止基準が達成された場合の停止理由を格納します。詳細は[`get_reason`](@ref)を参照してください。

# コンストラクタ

```
StopWhenModelIncreased()
```

# 参照

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
