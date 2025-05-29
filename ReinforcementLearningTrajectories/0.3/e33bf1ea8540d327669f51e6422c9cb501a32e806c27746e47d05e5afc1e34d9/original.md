```
InsertSampleRatioController(;ratio=1., threshold=1)
```

Used in [`Trajectory`](@ref). The `threshold` means the minimal number of insertings before sampling. The `ratio` balances the number of insertings and the number of samplings. For example a ratio of 1/10 will sample once every 10  insertings in the trajectory.
