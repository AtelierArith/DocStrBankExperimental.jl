```
transmutedims!(dst, src, perm⁺)
```

This is just `copy!(dst, transmute(src, perm⁺))`.
