```
annotate!(anns)
annotate!(anns::Tuple...)
annotate!(x, y, txt)
```

既存のプロットに注釈を追加します。注釈は、各 `(x,y,txt)` の形式のタプルのベクターとして指定するか、3つのベクター `x, y, txt` として指定します。各 `txt` は `String`、`PlotText`（`text(args...)` で作成）、または `text` への引数のタプル（例: `("Label", 8, :red, :top)`）であることができます。

# 例

```julia-repl
julia> plot(1:10)
julia> annotate!([(7,3,"(7,3)"),(3,7,text("hey", 14, :left, :top, :green))])
julia> annotate!([(4, 4, ("More text", 8, 45.0, :bottom, :red))])
julia> annotate!([2,5], [6,3], ["text at (2,6)", "text at (5,3)"])
```
