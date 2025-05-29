```
next_collision(p::AbstractParticle, bd::Billiard) -> i, tmin, cp
```

Compute the [`collision`](@ref) across all obstacles in `bd` and find the minimum one. Return the index of colliding obstacle, the time and the collision point.
