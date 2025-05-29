```
BatchStepsPerEpisode(batchsize::Int; tag = "TRAINING")
```

Similar to [`StepsPerEpisode`](@ref), but is specific to environments which return a `Vector` of rewards (a typical case with `MultiThreadEnv`).
