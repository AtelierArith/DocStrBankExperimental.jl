```
bvcomp(a, b)
bvcomp(a, bvconst(a, 0xffff, 16))
```

ビット単位の比較器: `a` と `b` のすべてのビットが等しい場合、`bvcomp(a,b) = 0b1`、そうでなければ `0b0`。
