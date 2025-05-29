```
SimulatorInferenceProblem(
    prob::SimulatorForwardProblem,
    forward_solver,
    prior::AbstractSimulatorPrior,
    likelihoods::AbstractLikelihood...;
    metadata::Dict=Dict(),
)
```

与えられたフォワード問題、事前分布、および尤度から `SimulatorInferenceProblem` を構築します。追加のユーザー指定メタデータは `metadata` 辞書に含めることができます。
