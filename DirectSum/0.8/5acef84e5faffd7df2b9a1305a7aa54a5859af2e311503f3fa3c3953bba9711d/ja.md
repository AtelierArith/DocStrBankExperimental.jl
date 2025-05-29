```
Single{V,G,B,T} <: TensorTerm{V,G,T} <: TensorGraded{V,G,T}
```

擬スカラー `V::Manifold` を持つ Single 型、グレード/ランク `G::Int`、`B::Submanifold{V,G}`、フィールド `T::Type`。
