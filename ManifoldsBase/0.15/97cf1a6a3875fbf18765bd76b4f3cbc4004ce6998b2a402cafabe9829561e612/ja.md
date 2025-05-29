```
copyto!(M::PowerManifoldNested, Y, p, X)
```

値を要素ごとにコピーします。すなわち、すべての要素 `A`、`a`、および `B` のために `copyto!(M.manifold, B, a, A)` を呼び出します。`X`、`p`、および `Y` のそれぞれに対して。
