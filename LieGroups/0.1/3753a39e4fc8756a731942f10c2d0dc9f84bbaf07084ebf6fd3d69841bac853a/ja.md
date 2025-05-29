```
isapprox(M::AbstractLieGroup, g, h; kwargs...)
```

点 `g` と `h` が [`AbstractLieGroup`](@ref) からおおよそ等しいかどうかを確認します。この関数は、1つ以上の点が [`Identity`](@ref) である場合の処理を行った後、対応する [`isapprox`](@extref `Base.isapprox-Tuple{AbstractManifold, Any, Any, Any}`) を [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) に対して呼び出します。すべてのキーワード引数はこの関数に渡されます。
