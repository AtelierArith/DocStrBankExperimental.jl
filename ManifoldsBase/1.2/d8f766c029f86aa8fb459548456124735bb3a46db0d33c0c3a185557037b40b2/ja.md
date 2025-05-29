```
IsIsometricManifoldEmbeddedManifold <: AbstractTrait
```

[`AbstractDecoratorManifold`](@ref) `M` が等長埋め込み多様体であるかどうかを判断するためのトレイトです。これは [`IsEmbeddedManifold`](@ref) トレイトの特別なケースであり、このトレイトのすべての特性を持っています。

ここでは、さらに、[`inner`](@ref) や [`norm`](@ref) のようなメトリック関連の関数が埋め込みに渡されます。
