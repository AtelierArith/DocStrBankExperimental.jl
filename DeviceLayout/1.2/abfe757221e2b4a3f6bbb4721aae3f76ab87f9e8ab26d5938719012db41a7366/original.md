```
HandedPointHook{T} <: Hook{T}
    h::PointHook{T}
    right_handed::Bool
```

A `PointHook` augmented with handedness.

In addition to translation and rotation, which are used to fuse one `PointHook` to another, a `HandedPointHook` being fused to another `HandedPointHook` will apply a reflection if necessary to match its handedness.
