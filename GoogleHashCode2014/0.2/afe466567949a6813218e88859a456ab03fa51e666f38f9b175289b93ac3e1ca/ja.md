```
plot_streets(
    city::City, solution::Union{Solution,Nothing}=nothing;
    path::Union{AbstractString,Nothing}=nothing,
    tiles::AbstractString="Cartodb Positron",
    zoom_start::Integer=12,
)
```

[`City`](@ref) とオプションの [`Solution`](@ref) を Python ライブラリ [`folium`](https://python-visualization.github.io/folium/) を使用してプロットし、結果を `path` に HTML ファイルとして保存します。

`folium` に渡される追加のパラメータには以下が含まれます：

  * 地図を装飾するために使用される `tiles` のセット
  * 初期ズームレベル `zoom_start`

このメソッドはパッケージ拡張で定義されており、PythonCall.jl をロードする必要があります。
