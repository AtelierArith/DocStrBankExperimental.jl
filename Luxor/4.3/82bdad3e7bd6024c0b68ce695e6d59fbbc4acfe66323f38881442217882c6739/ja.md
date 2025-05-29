```
GridRect(startpoint, xspacing, yspacing, width, height)
```

矩形グリッドを定義し、`startpoint`から始めてx軸に沿って`xspacing`のステップで進み、その後y軸に沿って`yspacing`のステップで進みます。

```
GridRect(startpoint, xspacing=100.0, yspacing=100.0, width=1200.0, height=1200.0)
```

列の場合、`xspacing`を0に設定します：

```
grid = GridRect(O, 0, 40)
```

グリッドからポイントを取得するには、`nextgridpoint(g::Grid)`を使用します。

```julia
julia> grid = GridRect(O, 0, 40);

julia> nextgridpoint(grid)
Point(0.0, 0.0)

julia> nextgridpoint(grid)
Point(0.0, 40.0)
```

グリッドポイントがなくなると、ラップして再び始まります。
