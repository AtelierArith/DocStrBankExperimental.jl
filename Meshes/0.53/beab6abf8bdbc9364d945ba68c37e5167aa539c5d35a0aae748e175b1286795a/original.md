```
∠(A, B, C)
```

Angle ∠ABC between rays BA and BC. See [https://en.wikipedia.org/wiki/Angle](https://en.wikipedia.org/wiki/Angle).

Uses the two-argument form of `atan` returning value in range [-π, π] in 2D and [0, π] in 3D. See [https://en.wikipedia.org/wiki/Atan2](https://en.wikipedia.org/wiki/Atan2).

## Examples

```julia
∠(Point(1,0), Point(0,0), Point(0,1)) == π/2
```
