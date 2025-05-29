```
is_identity(G::AbstractDecoratorManifold, q; kwargs)
```

`q`が[`IsGroupManifold`](@ref) `G`の単位元であるかどうかを確認します。つまり、対応する[`AbstractGroupOperation`](@ref) `O`を持つ[`Identity`](@ref)`{O}`であるか、（おおよそ）正しい点の表現である必要があります。
