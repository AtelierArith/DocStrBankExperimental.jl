```
swizzle!(v, value, indices...)
```

Mutate `v` at `indices` such that `v[i₁] = value[1], v[i₂] = value[2], ...` where `indices = (i₁, i₂, ...)`. and return `value`.

If any indices are duplicated in `indices`, `v` will be consecutively overwritten at the corresponding index, retaining the last value per the semantics of `setindex!`.
