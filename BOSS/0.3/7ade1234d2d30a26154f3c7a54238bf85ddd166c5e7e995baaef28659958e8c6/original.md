```
RandomAM()
```

Selects a random interior point instead of maximizing the acquisition function. Can be used for method comparison.

Can handle constraints on `x`, but does so by generating random points in the box domain until a point satisfying the constraints is found. Therefore it can take a long time or even get stuck if the constraints are very tight.
