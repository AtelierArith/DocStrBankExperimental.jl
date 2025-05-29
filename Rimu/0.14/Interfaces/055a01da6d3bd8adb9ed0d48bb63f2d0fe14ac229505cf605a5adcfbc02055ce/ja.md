```
step_stats(::StochasticStyle)
step_stats(::CompressionStrategy)
```

タプルの統計名（`Symbol`または`String`）と同じ長さのゼロのタプルを返します。これらは[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem)によって返される`DataFrame`の列として報告されます。
