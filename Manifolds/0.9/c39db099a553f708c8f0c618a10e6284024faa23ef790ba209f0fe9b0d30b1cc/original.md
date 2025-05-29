```
rand(::GroupManifold; vector_at=nothing, σ=1.0)
rand!(::GroupManifold, pX; vector_at=nothing, kwargs...)
rand(::TraitList{IsGroupManifold}, M; vector_at=nothing, σ=1.0)
rand!(TraitList{IsGroupManifold}, M, pX; vector_at=nothing, kwargs...)
```

Compute a random point or tangent vector on a Lie group.

For points this just means to generate a random point on the underlying manifold itself.

For tangent vectors, an element in the Lie Algebra is generated.
