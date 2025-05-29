```
intersect_geometry(line1::Line2D, line2::Line2D; atol=1e-6)
```

交差点が存在する場合はその点を返し、平行または重なっている場合は何も返しません。

直線の方程式は `ax + by = c` です。

交差点は次の方程式の解です：

```
|a1 b1 | | x | = | c1 |
|a2 b2 | | y |   | c2 |
```
