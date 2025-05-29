```
∠(u, v)
```

Angle between vectors `u` and `v`.

Uses the two-argument form of `atan` returning value in range [-π, π] in 2D and [0, π] in 3D. See [https://en.wikipedia.org/wiki/Atan2](https://en.wikipedia.org/wiki/Atan2).

## Examples

```julia
∠(Vec(1,0), Vec(0,1)) == π/2
```
