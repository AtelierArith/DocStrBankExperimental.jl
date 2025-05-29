```
boruvka_mst(g, distmx = weights(g); minimize = true)
```

最適な（デフォルトでは最小の）スパニングツリーを表すエッジのベクトル `mst` と、解のすべてのエッジの合計である `weights` を返すタプル `(mst, weights)` を返します。これは、異なるエッジの重みを提供するオプションの行列 `distmx` を持つ連結無向グラフ `g` に対して、[ボルブカのアルゴリズム](https://en.wikipedia.org/wiki/Bor%C5%AFvka%27s_algorithm)を使用して生成されます。このアルゴリズムは、最小/最大スパニングツリーを正しく生成するために、すべてのエッジが異なる重みを持つ必要があります。

### オプションの引数

  * `minimize=true`: `false` に設定すると、最大スパニングツリーを計算します。
