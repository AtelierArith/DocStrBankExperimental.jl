```
ones_gridgrad(::BasicILMCache,dim)
```

Get an instance of the gradient of the grid data in the cache, in direction `dim`, with values set to unity. If the data are of type `TensorGridData`, then `dim` takes values from 1 to 2^2.
