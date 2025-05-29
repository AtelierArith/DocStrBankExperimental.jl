```
InfiniteTimeReward{R <: Real, AR <: AbstractArray{R}}
```

`InfiniteTimeReward` is a property of rewards assigned to each state at each iteration and a discount factor for guaranteed convergence. The time horizon is infinite, i.e. $H = \infty$, so the optimal policy will be stationary.
