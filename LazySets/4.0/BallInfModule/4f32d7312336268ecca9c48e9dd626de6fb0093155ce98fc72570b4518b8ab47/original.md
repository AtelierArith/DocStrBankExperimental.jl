# Extended help

```
volume(B::BallInf)
```

### Algorithm

We compute the volume by iterative multiplication of the radius.

For floating-point inputs we use this implementation for balls of dimension less than $50$. For balls of higher dimension we instead compute $exp(n * log(2r))$, where $r$ is the radius of the ball.
