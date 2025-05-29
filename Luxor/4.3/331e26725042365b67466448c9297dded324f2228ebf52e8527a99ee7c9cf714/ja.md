```
slope(pointA::Point, pointB::Point)
```

`pointA`から`pointB`までの線の角度を求めます。

0から2πの間の値を返します。値は現在の軸に対して相対的です。

```julia
julia> slope(O, Point(0, 100)) |> rad2deg # yはページの下に向かって正
90.0

julia> slope(Point(0, 100), O) |> rad2deg
270.0
```

スロープは勾配とは異なります。上に向かう垂直な線は3π/2のスロープを持っています。
