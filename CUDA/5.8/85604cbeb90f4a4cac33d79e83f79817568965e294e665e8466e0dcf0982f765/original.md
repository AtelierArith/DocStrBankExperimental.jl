```
lanemask(pred)::UInt32
```

Returns a 32-bit mask indicating which threads in a warp satisfy the given predicate. Supported predicates are `==`, `<`, `<=`, `>=`, and `>`.
