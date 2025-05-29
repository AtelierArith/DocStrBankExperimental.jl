```
local_bound(G::Array{T,N}; correlation = N < 4, marg = true)
```

多項体ベル関数 `G` のローカルバウンドを計算します。`G` は `N` 次元配列として与えられます。`correlation` が `false` の場合、`G` は確率表記で書かれていると仮定されます。`correlation` が `true` の場合、`G` は相関表記で書かれていると仮定され、`marg` に応じて周辺分布が含まれる場合と含まれない場合があります。

参考文献: Araújo, Hirsch, Quintino, [arXiv:2005.13418](https://arxiv.org/abs/2005.13418)
