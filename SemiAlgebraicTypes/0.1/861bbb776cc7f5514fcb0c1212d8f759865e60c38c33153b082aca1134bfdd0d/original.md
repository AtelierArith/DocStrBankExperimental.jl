Mesh of the parametric surface f: (u,v) -> [x,y,z] for u in the interval U, v in the interval V. **Example**

```
mesh((u,v)->[u,v,cos(2*u*v)], 0.0 => 2.0, -pi => pi, field=DistField(0.0,0.0,0.0))
```
