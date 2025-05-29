```
inpoly(PolyX::Vector, PolyY::Vector, x::Number, y::Number, iSteps::Vector, jSteps::)
```

Checks if a point given by x and y is in or on (both cases return true) a polygon given by PolyX and PolyY, iSteps and jSteps provide the connectivity between the polygon edges. This function should be used through inpolygon!().
