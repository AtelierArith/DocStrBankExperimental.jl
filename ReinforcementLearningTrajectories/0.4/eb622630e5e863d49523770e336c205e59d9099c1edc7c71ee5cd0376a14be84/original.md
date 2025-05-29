```
EpisodeSampleRatioController(;ratio=1., threshold=1)
```

Used in [`Trajectory`](@ref). The `threshold` means the minimal number of episodes completed before sampling is allowed. The `ratio` balances the number of episodes and the number of samplings. For example a ratio of 1/10 will sample once every 10  episodes in the trajectory. Currently only works for environemnts with terminal states. 
