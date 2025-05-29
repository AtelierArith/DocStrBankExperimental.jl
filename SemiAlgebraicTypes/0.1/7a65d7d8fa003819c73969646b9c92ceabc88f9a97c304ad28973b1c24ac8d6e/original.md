Mesh of the parametric curve f: u -> [x(u),y(u),z(u)] for u in the interval U.

```
c = mesh(u->[u,sin(u^2),cos(2*u)], 0.0 => 2.0*pi, 1000; field=DistField(0.0,0.0,0.0))
```
