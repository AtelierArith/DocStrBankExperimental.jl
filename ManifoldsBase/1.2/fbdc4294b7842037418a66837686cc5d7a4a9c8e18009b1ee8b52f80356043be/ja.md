```
base_manifold(M::AbstractManifold, depth = Val(-1))
```

装飾された多様体 `M` の内部に保存されている [`AbstractManifold`](@ref) と、ベクトルバンドルやパワー多様体の基底多様体を返します。オプションのパラメータ `depth` は、最初の `depth` 個のデコレーターのみを削除し、そのレベルからの [`AbstractManifold`](@ref) を返すために使用できます。装飾されているかどうかにかかわらず、負の値はこの深さ制限を無効にします。
