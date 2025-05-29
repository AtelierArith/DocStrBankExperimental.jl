```
point(ray::AbstractRay{T,N}, alpha::T) -> SVector{T, N}
```

Returns a point on the ray at origin + alpha * direction. Alpha must be >= 0.
