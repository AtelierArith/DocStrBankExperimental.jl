```
plotannotatedframe(linked_data::AbstractDataFrame, filename::AbstractString, framenumber::Int; showimage=true, showellipse=true, plotkwargs...)
```

すべてのマイクロボットの軌跡が重ねられたビデオの単一フレームを表示します。オプションで、フィットした楕円や画像を非表示にすることができます。

単一のマイクロボットの軌跡をプロットするには、[`plotannotatedframe_single`](@ref)を使用してください。`plotkwargs`は`plot!()`に渡され、プロットの外観を変更することを目的としています。
