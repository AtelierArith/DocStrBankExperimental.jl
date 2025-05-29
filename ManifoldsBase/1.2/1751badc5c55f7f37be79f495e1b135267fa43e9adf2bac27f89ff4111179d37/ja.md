```
IsEmbeddedSubmanifold <: AbstractTrait
```

[`AbstractDecoratorManifold`](@ref) `M` が埋め込まれた部分多様体であるかどうかを判断するためのトレイトです。これは [`IsIsometricEmbeddedManifold`](@ref) トレイトの特別なケースであり、このトレイトのすべての特性を持っています。

このトレイトでは、等長埋め込まれた多様体に加えて、すべてのリトラクション、逆リトラクション、およびベクトル輸送、特に [`exp`](@ref)、[`log`](@ref)、および [`parallel_transport_to`](@ref) が埋め込みに渡されます。
