```
RandomWalk1D(;rewards=-1. => 1.0, N=7, start_pos=(N+1) ÷ 2, actions=[-1,1])
```

An agent is placed at the `start_pos` and can move left or right (stride is defined in actions). The game terminates when the agent reaches either end and receives a reward correspondingly.

Compared to the [`MultiArmBanditsEnv`](@ref):

1. The state space is more complicated (well, not that complicated though).
2. It's a sequential game of multiple action steps.
3. It's a deterministic game instead of stochastic game.
