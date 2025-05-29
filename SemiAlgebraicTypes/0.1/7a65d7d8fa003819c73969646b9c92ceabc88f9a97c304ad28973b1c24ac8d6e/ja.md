パラメトリック曲線 f: u -> [x(u),y(u),z(u)] のメッシュ、u は区間 U にあります。

```
c = mesh(u->[u,sin(u^2),cos(2*u)], 0.0 => 2.0*pi, 1000; field=DistField(0.0,0.0,0.0))
```
