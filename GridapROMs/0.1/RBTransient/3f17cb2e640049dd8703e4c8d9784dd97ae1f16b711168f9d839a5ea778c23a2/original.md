```
struct TransientProjection <: Projection
  projection_space::Projection
  projection_time::Projection
end
```

Projection operator for transient problems, containing a spatial projection and a temporal one. The space-time projection operator is equal to

`projection_time ⊗ projection_space`

which, for efficiency reasons, is never explicitly computed
