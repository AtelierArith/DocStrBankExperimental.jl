```
profit(anp::AbstractNewsvendorProblem)
```

Compute expected profit when stocking quantity q_opt.

```
profit(anp::AbstractNewsvendorProblem, q)
```

Compute expected profit when stocking quantity q. It is given by

$$
E[\textrm{profit}] = \textrm{underage cost} \times  \mu - E[\textrm{mismatch cost}] +  \textrm{profit shift}
$$
