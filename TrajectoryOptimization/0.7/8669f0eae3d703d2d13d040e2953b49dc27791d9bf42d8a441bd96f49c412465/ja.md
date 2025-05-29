```
CircleConstraint{P,T}
```

形の制約 $(x - x_c)^2 + (y - y_c)^2 \geq r^2$ で、$x$, $y$ は `x[xi]`,`x[yi]` で与えられ、$(x_c,y_c)$ は円の中心、$r$ は半径です。

# コンストラクタ:

```julia
CircleConstraint(n, xc::SVector{P}, yc::SVector{P}, radius::SVector{P}, xi=1, yi=2)
```
