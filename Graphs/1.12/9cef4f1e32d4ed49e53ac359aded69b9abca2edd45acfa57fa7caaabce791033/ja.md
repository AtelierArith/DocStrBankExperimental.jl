```
gdistances!(g, source, dists; sort_alg=QuickSort)
```

`dists`を、ソース頂点（または頂点のコレクション）`source`からのグレード距離で埋めます。`dists`は、`nv(g)`の長さを持つベクトルで、`typemax(T)`で埋められるべきです。`dists`を返します。

切断されたコンポーネントの頂点に対して、デフォルトの距離は`typemax(T)`です。

オプションのソートアルゴリズムを指定することができます（パフォーマンスセクションを参照）。

### パフォーマンス

`gdistances`は、デフォルトのソートアルゴリズムとして内部で`QuickSort`を使用します。これは、Julia Baseに組み込まれているアルゴリズムの中で最もパフォーマンスが良いためです。ただし、`RadixSort`（[SortingAlgorithms.jl](https://github.com/JuliaCollections/SortingAlgorithms.jl)を介して利用可能）を渡すことで、大規模なグラフにおいて大幅なパフォーマンス向上が得られます。 ```
