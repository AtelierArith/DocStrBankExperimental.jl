```
OfflineBehavior(; agent:: Union{<:Agent, Nothing}, steps::Int, reset_condition)
```

オフラインエージェントに「行動エージェント」を提供するために使用され、`PreExperimentStage`でトレーニングデータを生成します。`agent`が`nothing`（デフォルト）である場合、何もしません。エージェントの`trajectory`は親の`OfflineAgent`のものと同じである必要があります。`steps`は生成するデータ要素の数で、デフォルトは軌道の容量です。`reset_condition`はデータ生成のためのエピソードリセット条件で、デフォルトは`ResetIfEnvTerminated()`です。

行動エージェントは、データを生成するために実験のメイン環境と相互作用します。
