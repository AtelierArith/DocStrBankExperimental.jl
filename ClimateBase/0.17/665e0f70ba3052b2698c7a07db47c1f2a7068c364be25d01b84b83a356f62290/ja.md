```
collapse(f, A, dim)
```

次元 `dim` に向かって `A` を縮小し、縮小関数 `f`（例えば `mean`）を使用します。これは、`f` が `A` の他のすべての次元に適用され、それぞれがその後削除され、残りの次元に対する `A` の縮小結果のみが残ることを意味します。
