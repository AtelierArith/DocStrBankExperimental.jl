```
Projector(name=projector) <: PostStepStrategy
```

After each step, compute `dot(projector, dv)` and report it in the `DataFrame` under `name`. `projector` can be an [`AbstractDVec`](@ref), or an [`AbstractProjector`](@ref).
