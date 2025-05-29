```
epsilon_net(X, ϵ; metric)
```

Cover the PointCloud X with balls of radius ϵ. Returns the vector of indexes of X that are the ball's centers.

## Details

We start by covering the first point of X with an ϵ-ball. Then we search for the next point of X that is not covered by this ball. We repeat the process, until all points are inside a ball.
