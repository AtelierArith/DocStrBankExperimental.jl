```
Ball{T,C} <: Domain{T}
```

Abstract supertype for volumes of elements satisfying `norm(x-center(ball)) < radius(ball)` (open ball) or `norm(x-center(ball)) <= radius(ball)` (closed ball).
