```
System([derived,] priors, [images,] [propermotionanom,] planets..., name=:symbol)
```

Construct a model of a system. Must be constructed with a block of priors, and optionally additional derived parameters. You may provide `ProperMotionAnomLikelihood()` and/or `Images()` of the system. Finally, planet models are listed last. `name` must be a symbol e.g. `:HD56441`.
