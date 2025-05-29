```
struct AngleAxis{T} <: Rotation{3,T}
AngleAxis(Θ, x, y, z)
```

A 3×3 rotation matrix parameterized by a 3D rotation by angle θ about an arbitrary axis `[x, y, z]`.

Note that the axis is not unique for θ = 0, and that this parameterization does not continuously map the neighbourhood of the identity rotation (and therefore might not be suitable for autodifferentation and optimization purposes).

Note: by default, the constructor will renormalize the input so that the axis has length 1 (x² + y² + z² = 1).

Renormalization can be skipped by passing `false` as an additional constructor argument, in which case the user provides the guarantee that the input arguments represent a normalized rotation axis. Operations on an `AngleAxis` with a rotation axis that does not have unit norm, created by skipping renormalization in this fashion, are not guaranteed to do anything sensible.
