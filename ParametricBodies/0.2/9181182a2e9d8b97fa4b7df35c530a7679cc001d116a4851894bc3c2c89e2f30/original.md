```
d,n,V = measure(body::AbstractParametricBody,x,t)
```

Determine the geometric properties of the body at time `t` closest to  point `x`. Both `dot(curve)` and `dot(map)` contribute to `V` if defined.
