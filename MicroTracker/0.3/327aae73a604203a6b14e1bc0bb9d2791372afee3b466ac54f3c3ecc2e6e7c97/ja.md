```
plotannotatedframe_single(linked_data::AbstractDataFrame, particle_unique::AbstractString, framenumber::Int; showimage=true, showellipse=true, plotkwargs...)
```

ビデオの単一フレームを表示し、選択したマイクロボットの軌跡をオーバーレイします。オプションで、フィットした楕円や画像を非表示にすることができます。

すべてのマイクロボットの軌跡をプロットするには、[`plotannotatedframe`](@ref)を使用してください。`plotkwargs`は`plot!()`に渡され、プロットの外観を変更することを目的としています。
