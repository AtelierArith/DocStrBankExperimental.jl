```
minimum_cut(g, s, t, capacity_matrix=DefaultCapacity(); kws...)
```

有向グラフ `g` の `capacities` 行列に従って最小重みの `s-t cut` を見つけます。解は最大フローアルゴリズムを通じて見つかります。オプションの引数については [`maximum_flow`](@ref) を参照してください。

三つ組 `(f, cut, labels)` を返します。ここで `f` はカットの重み、`cut` はカット内のエッジのベクトル、`labels` はカットに従って二つのセットに分割された頂点を示します。
