```
Path3D(points;label="",pen=Pen(),arrow="",spline=false)
```

二次元パスを表すグラフィックスプリミティブ

`points` は `Vec3` の配列または 3-タプルの配列である可能性があります。あるいは、座標のイテラブルを `x` と `y` として別々に提供することもできます。

# 例

```julia-repl
julia> Path3D([(0,0),(1,0),(1,1)];pen="MidnightBlue")
```
