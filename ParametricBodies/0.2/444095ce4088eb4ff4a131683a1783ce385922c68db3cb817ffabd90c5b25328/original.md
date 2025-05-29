```
d = sdf(body::AbstractParametricBody,x,t)
```

Signed distance from `x` to closest point on `body.curve` at time `t`. Sign depends on the winding direction of the parametric curve.
