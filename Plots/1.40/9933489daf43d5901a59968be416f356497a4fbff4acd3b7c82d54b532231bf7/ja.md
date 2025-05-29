```
areaplot([x,] y)
areaplot!([x,] y)
```

行列 y のスタックエリアプロットを描画します。

# 例

```julia-repl
julia> areaplot(1:3, [1 2 3; 7 8 9; 4 5 6], seriescolor = [:red :green :blue], fillalpha = [0.2 0.3 0.4])
```
