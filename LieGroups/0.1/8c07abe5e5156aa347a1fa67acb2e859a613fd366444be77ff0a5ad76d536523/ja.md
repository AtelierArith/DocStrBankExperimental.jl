```
AbstractLieGroupPoint <: ManifoldsBase.AbstractManifoldPoint end
```

[`AbstractLieGroup`](@ref) 上の点のための抽象型です。点と接ベクトルは通常、柔軟性のために型なしで保持されますが、異なるタイプの点を区別する必要がある場合があります。例えば、

  * 構造体を必要とする複雑な表現のため
  * 意味的検証
  * 異なる表現が存在する場合

[`AbstractManifoldPoint`](@extref `ManifoldsBase.AbstractManifoldPoint`) をサブタイプ化することで、これは [`ManifoldsBase.jl`](https://juliamanifolds.github.io/ManifoldsBase.jl/) の同じアイデアに従います。
