```
cut_size(g::AbstractGraph, config; weights=UnitWeight(ne(g)))
```

グラフ `g` のカットのサイズを、構成 `config` を用いて返します。構成は、頂点のグループインデックスとしてのブール数のベクトルです。異なるグループの頂点間のエッジはカットとしてカウントされます。
