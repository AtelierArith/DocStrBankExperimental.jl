```
inpolygon!(INSIDE::Matrix, PolyX::Vector, PolyY::Vector, X::Matrix, Y::Matrix; fast=false)
```

Checks if points given by matrices `X` and `Y` are in or on (both cases return true) a polygon given by `PolyX` and `PolyY`. Boolean `fast` will trigger faster version that may miss points that are exactly on the edge of the polygon. Speedup is a factor of 3.
