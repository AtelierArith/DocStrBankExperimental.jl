```
self_avoiding_walk(g, s, niter; seed=-1)
```

グラフ `g` 上で、頂点 `s` から始めて最大 `niter` ステップの間、[自己回避ウォーク](https://en.wikipedia.org/wiki/Self-avoiding_walk) を実行します。訪れた頂点のベクトルを順番に返します。
