```
BasicBody(x,y[,closuretype=ClosedBody]) <: Body
```

Construct a body by simply passing in the `x` and `y` coordinate vectors. The last point will be automatically connected to the first point. The coordinate vectors are assumed to be expressed in the body-fixed coordinate system. The optional `closuretype` specifies whether the body is closed (`ClosedBody`) or open (`OpenBody`). If closed, then the first and last points are assumed joined in operations that require neighbor points.
