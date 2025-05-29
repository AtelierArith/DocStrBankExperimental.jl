```
random_bipartite_configuration_model(
                                n1::Int, n2::Int, 
                                k1::Vector{Int}, k2::Vector{Int}, 
                                G=Graph; seed=-1)
```

[構成モデル](http://tuvalu.santafe.edu/~aaronc/courses/5352/fall2013/csci5352_2013_L11.pdf) に従ってランダムな二部無向グラフを作成します。これは `n1+n2` の頂点を含みます。最初のセットの頂点 `i` は次数 `k1[i]` を持ち、二番目のセットの頂点 `i` は次数 `k2[i]` を持ちます。

`G` は結果として得られるグラフの型です。
