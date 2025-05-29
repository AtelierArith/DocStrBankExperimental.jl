```
boxmap(A::Array, pt, w, h)
```

`A`の値を使って、`pt`に1つのコーナーがあり、幅`w`と高さ`h`のボックスマップを構築します。ボックスの数は`length(A)`です。ボックスの面積は元の値に比例し、必要に応じてスケーリングされます。

戻り値は`BoxmapTiles`の配列です。例えば：

```julia
[BoxmapTile(0.0, 0.0, 10.0, 20.0)
 BoxmapTile(10.0, 0.0, 10.0, 13.3333)
 BoxmapTile(10.0, 13.3333, 10.0, 6.66667)]
```

各タイルは`(x, y, w, h)`を含みます。`box()`および`BoundingBox()`はBoxmapTilesでも動作します。

# 例

```julia
using Luxor
@svg begin
    fontsize(16)
    fontface("HelveticaBold")
    pt = Point(-200, -200)
    a = rand(10:200, 15)
    tiles = boxmap(a, Point(-200, -200), 400, 400)
    for (n, t) in enumerate(tiles)
        randomhue()
        bb = BoundingBox(t)
        box(bb - 2, :stroke)
        box(bb - 5, :fill)
        sethue("white")
        text(string(n), midpoint(bb[1], bb[2]), halign=:center)
    end
end 400 400 "boxmap.svg"
```
