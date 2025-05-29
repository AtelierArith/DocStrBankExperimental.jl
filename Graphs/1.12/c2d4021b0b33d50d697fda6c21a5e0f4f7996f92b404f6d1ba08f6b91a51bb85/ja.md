```
yen_k_shortest_paths(g, source, target, distmx=weights(g), K=1; maxdist=typemax(T));
```

グラフ上で[Yenのアルゴリズム](http://en.wikipedia.org/wiki/Yen%27s_algorithm)を実行し、`source`と`target`の間のk短距離を計算します。他の頂点との距離と経路を含む[`YenState`](@ref)を返します。
