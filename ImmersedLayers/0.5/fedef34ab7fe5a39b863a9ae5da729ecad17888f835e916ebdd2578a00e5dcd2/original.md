```
mask(cache::BasicILMCache) -> GridData
mask(sys::ILMSystem) -> GridData
```

Create grid data that consist of 1s inside of a surface (i.e., on a side opposite   the normal vectors) and 0s outside. The grid data are the same type as the   output data type of `sys`.  Only allows `sys` to have `GridScaling`.   If the cache has no immersed surface, then it reverts to 1s everywhere.
