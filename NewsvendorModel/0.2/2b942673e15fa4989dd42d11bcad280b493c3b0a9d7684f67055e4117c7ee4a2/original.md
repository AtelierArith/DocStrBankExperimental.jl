```
mismatch_cost(anp::AbstractNewsvendorProblem, q)
```

Compute expected mismatch cost when stocking quantity q. It is given by

$$
E[\textrm{mismatch cost}] = \textrm{underage cost} \times  E[\textrm{lost sales}] + \textrm{overage cost} \times  E[\textrm{leftover}]
$$
