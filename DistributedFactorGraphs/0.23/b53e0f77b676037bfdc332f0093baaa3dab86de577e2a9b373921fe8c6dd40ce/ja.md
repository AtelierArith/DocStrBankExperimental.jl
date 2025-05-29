```
@defVariable StructName manifolds<:ManifoldsBase.AbstractManifold
```

`StructName`という名前の新しい変数を作成するためのマクロであり、`manifolds`はオブジェクトであり、*必ず* `ManifoldsBase.AbstractManifold`のサブタイプでなければなりません。詳細は[Manifolds.jl on making your own](https://juliamanifolds.github.io/Manifolds.jl/stable/examples/manifold.html)のドキュメントを参照してください。

例:

```
DFG.@defVariable Pose2 SpecialEuclidean(2) ArrayPartition([0;0.0],[1 0; 0 1.0])
```
