```
CircleConstraint{P,T}
```

Constraint of the form $(x - x_c)^2 + (y - y_c)^2 \geq r^2$ where $x$, $y$ are given by `x[xi]`,`x[yi]`, $(x_c,y_c)$ is the center of the circle, and $r$ is the radius.

# Constructor:

```julia
CircleConstraint(n, xc::SVector{P}, yc::SVector{P}, radius::SVector{P}, xi=1, yi=2)
```
