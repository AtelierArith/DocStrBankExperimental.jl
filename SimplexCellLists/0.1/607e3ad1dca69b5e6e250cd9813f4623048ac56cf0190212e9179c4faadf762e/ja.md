すべてのSimplexCellList実装のための抽象型。

実装は、次のようなシグネチャのコンストラクタを持たなければなりません。

```julia
T(numpointgroups::Integer, numlinegroups::Integer, numtrianglegroups::Integer; kwargs...)::T
```

ここで、`numpointgroups`は点のグループの数、`numlinegroups`は線のグループの数、`numtrianglegroups`は三角形のグループの数です。

`kwargs`は`T`に特有のオプションです。
