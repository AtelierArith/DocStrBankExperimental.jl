```
kruskal_mst(g, distmx=weights(g); minimize=true)
```

接続された無向グラフ `g` の最小（デフォルト）スパニングツリーを表すエッジのベクトルを返します。オプションの距離行列 `distmx` を使用して、[クラスカルのアルゴリズム](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm)を利用します。

### オプション引数

  * `minimize=true`: `false` に設定すると、最大スパニングツリーを計算します。
