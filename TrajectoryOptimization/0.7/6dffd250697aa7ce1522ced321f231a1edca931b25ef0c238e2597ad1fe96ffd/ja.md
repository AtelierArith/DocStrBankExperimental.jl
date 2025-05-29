```
SphereConstraint{P,T}
```

形状の制約は $(x - x_c)^2 + (y - y_c)^2 + (z - z_c)^2 \geq r^2$ であり、ここで $x$, $y$, $z$ は `x[xi]`,`x[yi]`,`x[zi]` で与えられ、$(x_c,y_c,z_c)$ は球の中心、$r$ は半径です。

# コンストラクタ:

```
SphereConstraint(n, xc::SVector{P}, yc::SVector{P}, zc::SVector{P},
	radius::SVector{P}, xi=1, yi=2, zi=3)
```
