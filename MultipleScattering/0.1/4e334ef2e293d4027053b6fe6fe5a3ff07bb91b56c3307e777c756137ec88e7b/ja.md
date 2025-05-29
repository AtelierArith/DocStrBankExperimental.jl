```
FrequencySimulation([particles::AbstractParticles=[],]
                    source::AbstractSource)
```

FrequencySimulationを構築します。粒子が提供されていない場合、空の配列が使用されます。

構築後、シミュレーションを[`run`](@ref)して[`FrequencySimulationResult`](@ref)を取得できます。
