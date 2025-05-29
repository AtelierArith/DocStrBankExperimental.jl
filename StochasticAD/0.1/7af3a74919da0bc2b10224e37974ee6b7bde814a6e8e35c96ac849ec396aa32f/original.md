```
new_weight(p::Real)

Simulate a Bernoulli variable whose primal output is always 1. 
Uses a smoothing rule for use in forward and reverse-mode AD, which is exactly unbiased when the quantity is only
used in linear functions  (e.g. used as an [importance weight](https://en.wikipedia.org/wiki/Importance_sampling)).
```
