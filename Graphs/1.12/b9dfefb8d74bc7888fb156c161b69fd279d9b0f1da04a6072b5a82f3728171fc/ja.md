```
gdistances(g, source; sort_alg=QuickSort)
```

`g`の頂点から`source`までの測地線距離で満たされたベクトルを返します。`source`が頂点のコレクションである場合、各要素は一意である必要があります。切断された成分の頂点に対しては、デフォルトの距離は`typemax(T)`です。

オプションのソートアルゴリズムを指定することができます（パフォーマンスセクションを参照）。

### パフォーマンス

`gdistances`は、デフォルトのソートアルゴリズムとして内部で`QuickSort`を使用します。これは、Julia Baseに組み込まれているアルゴリズムの中で最もパフォーマンスが良いためです。ただし、`RadixSort`（[SortingAlgorithms.jl](https://github.com/JuliaCollections/SortingAlgorithms.jl)を介して利用可能）を渡すことで、大規模なグラフにおいて大幅なパフォーマンス向上が得られます。
