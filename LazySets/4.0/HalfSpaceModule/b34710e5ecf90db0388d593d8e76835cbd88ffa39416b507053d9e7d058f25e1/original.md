```
normalize(hs::HalfSpace{N}, p::Real=N(2)) where {N}
```

Normalize a half-space.

### Input

  * `hs` – half-space
  * `p`  – (optional, default: `2`) norm

### Output

A new half-space whose normal direction $a$ is normalized, i.e., such that $‖a‖_p = 1$ holds.
