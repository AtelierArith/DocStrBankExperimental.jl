```julia
kill_agent!(
    agent::EasyABM.AbstractAgent,
    model::EasyABM.AbstractSpaceModel{EasyABM.MortalType}
) -> Union{Nothing, Int64}

```

エージェントを非アクティブに設定し、モデルから効果的に削除します。ただし、削除されたエージェントは、`step_rule`の後にのみ`model.agents`のリストから永久に削除されます。
