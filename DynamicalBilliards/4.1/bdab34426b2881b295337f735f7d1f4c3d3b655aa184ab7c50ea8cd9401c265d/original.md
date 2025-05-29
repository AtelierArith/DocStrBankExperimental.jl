```
collision(p::AbstractParticle, o::Obstacle) → t, cp
```

Find the collision (if any) between given particle and obstacle. Return the time until collision and the estimated collision point `cp`.

Return `Inf, SV(0, 0)` if the collision is not possible *or* if the collision happens backwards in time.

**It is the duty of `collision` to avoid incorrect collisions when the particle is on top of the obstacle (or very close).**
