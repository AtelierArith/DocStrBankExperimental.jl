```
struct DafView(daf::DafReader) <: DafReader
```

A read-only wrapper for any [`DafReader`](@ref) data, which exposes an arbitrary view of it as another [`DafReadOnly`](@ref). This isn't typically created manually; instead call [`viewer`](@ref).
