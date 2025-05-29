```
prim_mst(g, distmx=weights(g))
```

接続された無向グラフ `g` の最小全域木を表すエッジのベクトルを返します。オプションの距離行列 `distmx` を使用して、[プリムのアルゴリズム](https://en.wikipedia.org/wiki/Prim%27s_algorithm)を使用します。エッジのベクトルを返します。
