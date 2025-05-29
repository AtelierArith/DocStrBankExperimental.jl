```
FiniteTimeReward{R <: Real, AR <: AbstractArray{R}, T <: Integer}
```

`FiniteTimeReward` is a property of rewards $R : S \to \mathbb{R}$ assigned to each state at each iteration and a discount factor $\gamma$. The time horizon $H$ is finite, so the discount factor is optional and  the optimal policy will be time-varying. Given a strategy $\pi : S \to A$, the property is

$$
    V(s_0) = \mathbb{E}\left[\sum_{k=0}^{H} \gamma^k R(s_k) \mid s_0, \pi\right].
$$
