```
complementary_mask!(w::GridData,cache::BasicILMCache)
complementary_mask!(w::GridData,sys::ILMSystem)
```

Mask the data `w` in place by multiplying it by 0s inside of a surface (i.e., on a side opposite   the normal vectors) and 1s outside. The grid data `w` must be of the same type as the   output data type of `cache`. Only allows `cache` to have `GridScaling`.
