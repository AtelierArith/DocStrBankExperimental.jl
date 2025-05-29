```
leftover(anp::AbstractNewsvendorProblem, q)
```

Compute expected leftover inventory when stocking quantity q.

$$
E[\textrm{leftover}] = \int_{-\infty}0^q(q - x)f(x)dx 
$$
