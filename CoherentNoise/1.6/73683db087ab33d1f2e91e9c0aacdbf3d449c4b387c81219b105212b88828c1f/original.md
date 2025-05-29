```
scale(source::AbstractSampler; x=1.0, y=1.0, z=1.0, w=1.0)
```

Construct a modifier sampler that scales the input coordinates of sampler `source` before sampling from it.

Each axis can be scaled independently with `x`, `y`, `z`, or `w`.
