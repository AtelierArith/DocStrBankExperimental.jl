```
PointRegionCache(pts::VectorData,cache::BasicILMCache[,kwargs])
```

Create a regularized point collection based on points `pts`, using the data in `cache` to provide the details of the regularization. The `kwargs` can be used to override the regularization choices, such as ddf.
