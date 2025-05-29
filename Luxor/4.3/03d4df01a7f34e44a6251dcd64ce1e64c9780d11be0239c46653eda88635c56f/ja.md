```
circlering(o_center, o_radius, count=3)
```

o_centerを中心とし、半径を持つ想像上の円の内側に収まる`count`個の円を見つけ、それに接する円を求めます。

返り値:

  * 各円を定義する中心/半径のタプルの配列
  * 計算された円の内側に収まる円を定義する単一の中心/半径のタプル

```julia
cs, ic = circlering(Point(0, 0), 200, 3)

(Tuple
    [(Point(-53.59246086870698, 92.82486512724742), 92.815078262586),
     (Point(-53.59246086870705, -92.82486512724739), 92.815078262586),
     (Point(107.184921737414, -2.6252734264516723e-14), 92.815078262586)
   ],
    (Point(0.0, 0.0), 14.369843474828002))

@draw begin
    cs, ic = circlering(Point(0, 0), 200, 3)
    map(c -> circle(first(c), last(c), :fill), cs)
    circle(first(ic), last(ic), :fill)
end
```
