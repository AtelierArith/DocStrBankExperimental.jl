```
copyto!(M::PowerManifoldNested, Y, p, X)
```

値を要素ごとにコピーします。すなわち、`X`、`p`、および`Y`のすべての要素`A`、`a`、および`B`に対して`copyto!(M.manifold, B, a, A)`を呼び出します。
