```
Edge(v1::RealVector, v2::RealVector; label::Int = 0)
```

Edge defined by two endpoints and a label which indicates the neighbor's index. Zero or negative indices are used for domain boundaries.  Edges are stack-allocated and immutable. 
