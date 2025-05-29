```
complementary_mask(cache::BasicILMCache) -> GridData
complementary_mask(sys::ILMSystem) -> GridData
```

Create grid data that consist of 0s inside of a surface (i.e., on a side opposite   the normal vectors) and 1s outside. The grid data are the same type as the   output data type of `cache`.  Only allows `cache` to have `GridScaling`.   If the cache has no immersed surface, then it reverts to 0s everywhere.
