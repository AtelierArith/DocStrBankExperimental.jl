```
StopWhenModelIncreased <: StoppingCriterion
```

モデル値の曲率が増加したかどうかをテストするファンクタ。

# フィールド

  * `at_iteration::Int`: 停止基準が最後に停止を示したイテレーションを示す整数。これはソルバーが開始する前（`0`）である可能性もあります。負の値は、まだそのようなことがなかったことを示します；
  * `model_value`は最後のモデル値を格納します
  * `inc_model_value`は増加したモデル値を格納します

# コンストラクタ

```
StopWhenModelIncreased()
```

# 参照

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
