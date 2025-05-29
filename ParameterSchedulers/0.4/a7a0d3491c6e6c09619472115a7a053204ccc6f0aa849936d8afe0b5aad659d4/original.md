```
CosAnneal(l0, l1, period, restart = true)
CosAnneal(; l0, l1, period, restart = true)
```

A cosine annealing schedule (see ["SGDR: Stochastic Gradient Descent with Warm Restarts"](https://arxiv.org/abs/1608.03983v5)) The output conforms to

```text
t̂ = restart ? mod(t - 1, period) : (t - 1)
abs(l0 - l1) * (1 + cos(π * t̂ / period)) / 2 + min(l0, l1)
```

This schedule is also referred to as "cosine annealing (with warm restarts)" in machine learning literature.

# Arguments

  * `range == abs(l0 - l1)`: the dynamic range (given by the endpoints)
  * `offset == min(l0, l1)`: the offset / minimum value
  * `period::Integer`: the period
  * `restart::Bool`: use warm-restarts
