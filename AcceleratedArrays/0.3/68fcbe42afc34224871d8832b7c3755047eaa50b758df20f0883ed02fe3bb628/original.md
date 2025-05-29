```
accelerate(a, IndexType)
```

Return an `AcceleratedArray` wrapping `a` using the acceleration index of type `T`.

This operation will not modify `a` but the acceleration index will be invalidated (and become unsafe to use) if `a` is modified directly after the index is constructed. (See also `accelerate!`).
