```
BatchStepsPerEpisode(batchsize::Int; tag = "TRAINING")
```

[`StepsPerEpisode`](@ref)と似ていますが、`Vector`の報酬を返す環境に特有です（`MultiThreadEnv`での典型的なケース）。
