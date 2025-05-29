```
DistL2(ind_S)
```

Given `ind_S` the indicator function of a set $S$, and an optional positive parameter `λ`, return the (weighted) Euclidean distance from $S$, that is function

$$
g(x) = λ\mathrm{dist}_S(x) = \min \{ λ\|y - x\| : y \in S \}.
$$
