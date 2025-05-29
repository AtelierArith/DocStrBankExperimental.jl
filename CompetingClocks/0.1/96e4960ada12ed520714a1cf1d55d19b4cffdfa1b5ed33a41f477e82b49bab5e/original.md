```
next(multiple_direct, when, rng)
```

Selects the next transition to fire and when it fires.

There are two main algorithms for this selection. This implementation handles the case when there are a lot of clocks or when some clocks have much smaller hazards. It first draws a random number to choose which subset of hazards will be used, and then it asks that subset to draw a random number to choose which particular hazard is used. When there are many hazards, it is possible that a random number generator will *never* choose a particular value because there is no guarantee that a random number generator covers every combination of bits. Using more draws decreases the likelihood of this problem.
