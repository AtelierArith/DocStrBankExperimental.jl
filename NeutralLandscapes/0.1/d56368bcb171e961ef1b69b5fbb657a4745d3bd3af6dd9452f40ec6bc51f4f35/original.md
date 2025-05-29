```
WaveSurface <: NeutralLandscapeMaker

WaveSurface(; direction=360rand(), periods=1)
WaveSurface(direction, [periods=1])
```

Creates a sinusoidal landscape with a `direction` and a number of `periods`. If neither are specified, there will be a single period of random direction.
