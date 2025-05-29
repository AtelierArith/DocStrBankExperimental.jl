```
rotate(source::AbstractSampler; x=0.0, y=0.0, z=0.0)
```

Construct a modifier sampler that rotates the input coordinates of sampler `source` around the origin before sampling from it.

The coordinate system is assumed to be left-handed.

The angle of rotation is specified in radians for the corresponding axis given by `x`, `y`, and `z`.
