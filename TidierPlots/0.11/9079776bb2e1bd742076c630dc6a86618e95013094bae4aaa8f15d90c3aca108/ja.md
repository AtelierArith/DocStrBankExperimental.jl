```
geom_tile(aes(...), ...)
geom_tile(plot::GGPlot, aes(...), ...)
```

矩形の集合としてヒートマップをプロットします。

# 詳細

`x`、`y`、および `z` はすべて同じ長さでなければならず、重複する (x, y) ペアは存在してはいけません。`x`、`y`、および `z` を `(x, y, f(x, y))` の形の三つ組と考えることができます。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト
  * `aes(...)`: マッピングに使用されるDataFrameの列の名前
  * `...`: 列にマッピングされていないオプション (Makie.Heatmapに渡される)

# 必須の美学

  * `x`
  * `y`
  * `z`

# オプションの美学 (see [`aes`](@ref))

  * NA

# オプションの引数

  * `interpolate=false`
  * `colormap` / `palette`
  * `alpha`

# 例

```julia
function mandelbrot(x, y)
    z = c = x + y*im
    for i in 1:30.0; abs(z) > 2 && return i; z = z^2 + c; end; 0
end

xs = -2:0.01:1
ys = -1.1:0.01:1.1
xys = Iterators.product(xs, ys) |> collect |> vec
zs = map(xy -> mandelbrot(xy[1], xy[2]), xys)

df = DataFrame(
    x = first.(xys),
    y = last.(xys),
    z = zs
)

ggplot(df, @aes(x = x, y = y, z = z)) + geom_tile()
```
