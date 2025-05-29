```
SphereConstraint{P,T}
```

Constraint of the form $(x - x_c)^2 + (y - y_c)^2 + (z - z_c)^2 \geq r^2$ where $x$, $y$, $z$ are given by `x[xi]`,`x[yi]`,`x[zi]`, $(x_c,y_c,z_c)$ is the center of the sphere, and $r$ is the radius.

# Constructor:

```
SphereConstraint(n, xc::SVector{P}, yc::SVector{P}, zc::SVector{P},
	radius::SVector{P}, xi=1, yi=2, zi=3)
```
