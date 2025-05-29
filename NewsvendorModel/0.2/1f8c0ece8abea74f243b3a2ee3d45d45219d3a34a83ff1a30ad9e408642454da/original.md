```
q_scarf(anp::AbstractNewsvendorProblem)
```

Compute the quanitity that maximizes the minimal expected profit among all  distributions with the same mean and variance. Worst-case solution (Scarf, 1958)

$$
q_{scarf} = \mu + \sigma/2 * (\sqrt{r} - \sqrt{1/r})
$$

where

$$
r = \frac{\textrm{underage cost}}{ \textrm{overage cost}}
$$
