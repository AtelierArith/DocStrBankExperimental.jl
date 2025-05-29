```
AbstractLieAlgebraTangentVector <: ManifoldsBase.AbstractTangentVector
```

[`LieAlgebra`](@ref)で表現された接ベクトルのための抽象型です。

接ベクトルは通常、柔軟性のために型なしで保持されますが、異なるタイプの点を区別する必要がある場合があります。例えば、

  * 構造体を必要とする複雑な表現の場合

@ semantic verification

  * 異なる表現が存在する場合

[`AbstractManifoldPoint`](@extref `ManifoldsBase.AbstractManifoldPoint`)をサブタイプ化することにより、これは[`ManifoldsBase.jl`](https://juliamanifolds.github.io/ManifoldsBase.jl/)の同じアイデアに従います。
