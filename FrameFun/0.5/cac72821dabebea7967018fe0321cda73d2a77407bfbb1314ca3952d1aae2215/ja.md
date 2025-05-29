```
struct ExtensionFrame{S,T} <: DerivedDict{S,T}
```

ExtensionFrameは、基底をその定義域の部分集合に制限したものです。これにより、より小さな集合上の関数の拡張をより大きな集合に暗黙的に表現するフレームが得られます。

関数`extensionframe`によって作成されます。

参照: [`extensionframe`](@ref)

```jldocs
julia> extensionframe(Fourier(10),0.0..0.5)
```
