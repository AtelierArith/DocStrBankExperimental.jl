```
struct MultiLogiset{L<:AbstractLogiset}
    modalities  :: Vector{L}
end
```

異なる[モダリティ](https://en.wikipedia.org/wiki/Multimodal_learning)で構成された論理データセット。この構造は、論理的な観点からマルチモーダルデータセットを表現するのに役立ちます。

関連項目としては、[`AbstractLogiset`](@ref)、[`minify`](@ref)があります。
