```
heatmap(x,y,z)
heatmap!(x,y,z)
```

矩形配列 `z` のヒートマップをプロットします。

# キーワード引数

  * `aspect_ratio::Union{Real, Symbol}`: プロット領域は、1 y単位が `aspect_ratio` x単位と同じサイズになるようにリサイズされます。`:none` の場合、画像はプロット領域のアスペクト比を継承します。単位アスペクト比には `:equal` を使用します。エイリアス: (:aspect*ratios, :aspectratio, :aspectratios, :axis*ratio, :axisratio, :ratio)。

# 例

```julia-repl
julia> heatmap(randn(10,10))
```
