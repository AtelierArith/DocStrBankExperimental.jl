```
JointPrior{modelPriorType<:AbstractSimulatorPrior,likNames,likPriorTypes,axesType} <: AbstractSimulatorPrior
```

「ジョイント」事前分布 `p(θₘ,θₗ)` を表し、ここで `θ = [θₘ θₗ]` はジョイント内のパラメータの完全なセットであり、分布 `p(x,θ)` です。θₘ はモデル（シミュレーター）パラメータであり、θₗ はノイズ/エラーモデルパラメータです。
