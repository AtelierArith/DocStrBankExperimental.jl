```
DepthDependantSinkingSpeed(; minimum_speed = 30/day,
                             maximum_speed = 200/day,
                             maximum_depth = 500)
```

Returns sinking speed for particles which sink at `minimum_speed` in the surface ocean (the deepest of the mixed and euphotic layers), and accelerate to `maximum_speed` below that depth and `maximum_depth`.
