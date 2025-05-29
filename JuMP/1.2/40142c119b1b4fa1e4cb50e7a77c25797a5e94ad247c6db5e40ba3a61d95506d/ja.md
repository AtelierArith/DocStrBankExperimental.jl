```
compute_conflict!(model::Model)
```

モデルが非可行である場合にコンフリクトを計算します。最適化プログラムがまだ設定されていない場合（[`set_optimizer`](@ref]を参照）、[`NoOptimizer`](@ref) エラーがスローされます。

コンフリクトのステータスは、`MOI.ConflictStatus` モデル属性を使用して確認できます。その後、各制約のステータスは `MOI.ConstraintConflictStatus` 属性を使用して照会できます。
