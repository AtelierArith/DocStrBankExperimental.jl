```
AbstractFace{N_indices, T} <: StaticVector{N_indices, T}
```

Parent type for all face types. The standard face type is typically a `GLTriangleFace = NgonFace{3, GLIndex}`.
