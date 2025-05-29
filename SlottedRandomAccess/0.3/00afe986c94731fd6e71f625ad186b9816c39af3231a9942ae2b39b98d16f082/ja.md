```julia
struct CRDSA{N} <: SlottedRandomAccess.FixedRepSlottedRAScheme{N}
```

*コンテンション解決多様性スロットALOHA* (CRDSA) スキームを表す型で、レプリカの数 `N` を持ちます。

このRAスキームは[この2007年のIEEE論文](https://doi.org/10.1109/TWC.2007.348337)で紹介されました。

参照: [`MF_CRDSA`](@ref)
