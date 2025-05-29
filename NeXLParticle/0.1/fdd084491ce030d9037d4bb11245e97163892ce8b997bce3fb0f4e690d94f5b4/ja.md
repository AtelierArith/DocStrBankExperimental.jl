```
asimage(dc::DiluvianCluster, colors::Vector{Colorant}, other = colorant"black")::Array{Colorant}
asimage(dc::DiluvianCluster)
```

最初の `length(colors)` クラスターが `colors` に従って色付けされ、残りが `other` で色付けされたカラフルな画像を取得します。2 番目のバージョンは、`distinguishable_colors(…)` を使用して自動的に十分な色を生成します。
