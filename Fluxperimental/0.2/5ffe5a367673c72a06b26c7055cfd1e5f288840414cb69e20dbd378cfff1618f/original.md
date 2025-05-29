```
Moonduo(x, [dx])
```

This stores both an object `x` and its gradient `dx`, with `dx` in the format used by Mooncake.jl. This is automatically allocated when you call `Moonduo(x)`.

This serves the same purpose as Enzyme.jl's `Duplicated` type. Both of these AD engines prefer that space for the gradient be pre-allocated.
