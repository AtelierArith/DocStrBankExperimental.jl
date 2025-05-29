Calculate the width of the confidence interval at a certain `p`-value. This is based on the paper:     Carvalho (2011), "Confidence intervals for the minimum of a     function using extreme value statistics"

This means that the current estimate of the confidence interval for the minimum of the optimized function lies within the interval

```
] l1 - w, l1 [
```

with probability $(1-p)$ as the number of sampled function points goes to infinity, where

```
w = width_of_confidence_interval(a, p)
l1 = best_fitness(a)
```
