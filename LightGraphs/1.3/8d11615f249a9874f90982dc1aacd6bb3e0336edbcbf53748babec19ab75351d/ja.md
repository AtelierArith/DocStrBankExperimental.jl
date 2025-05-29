```
yen_k_shortest_paths(g, source, target, distmx=weights(g), K=1; maxdist=Inf);
```

グラフ上で[Yenのアルゴリズム](http://en.wikipedia.org/wiki/Yen%27s_algorithm)を実行し、`source`と`target`の間のk短距離を計算します。距離とパスを含む[`YenState`](@ref)を返します。
