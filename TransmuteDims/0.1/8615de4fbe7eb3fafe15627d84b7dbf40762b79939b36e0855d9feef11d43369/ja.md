```
transmutedims!(dst, src, perm⁺)
```

これは単に `copy!(dst, transmute(src, perm⁺))` です。
