```
OfflineAgent(policy::AbstractPolicy, trajectory::Trajectory, offline_behavior::OfflineBehavior = OfflineBehavior()) <: AbstractAgent
```

`OfflineAgent`は、通常のオンライン`Agent`とは異なり、データを収集するためにトレーニング中に環境と相互作用しない`AbstractAgent`です。`Agent`と同様に、トレーニングされる`AbstractPolicy`とトレーニングデータを含む`Trajectory`を含んでいます。違いは、トレーニング前に軌跡が埋められ、更新されないことです。オプションで`OfflineBehavior`を提供することができ、`PreExperimentStage`でトレーニングデータを生成する第二の「行動エージェント」を提供します。デフォルトでは何もしません。
