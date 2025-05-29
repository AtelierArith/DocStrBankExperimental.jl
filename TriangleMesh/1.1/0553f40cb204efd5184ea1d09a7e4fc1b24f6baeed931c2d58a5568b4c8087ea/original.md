```
Polygon_pslg(n_point :: Int, n_point_marker :: Int, n_point_attribute :: Int, n_segment :: Int, n_hole :: Int, n_region :: Int)
```

Outer constructor that only reserves space for points, markers, attributes, holes and regions. Input data is converted to hold C-data structures (Cint and Cdouble arrays) for internal use.
