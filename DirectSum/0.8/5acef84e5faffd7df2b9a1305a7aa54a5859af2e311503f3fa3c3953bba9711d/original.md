```
Single{V,G,B,T} <: TensorTerm{V,G,T} <: TensorGraded{V,G,T}
```

Single type with pseudoscalar `V::Manifold`, grade/rank `G::Int`, `B::Submanifold{V,G}`, field `T::Type`.
