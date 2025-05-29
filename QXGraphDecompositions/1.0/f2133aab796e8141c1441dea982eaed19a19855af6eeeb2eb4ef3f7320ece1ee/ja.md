```
restricted_mcs(H::LabeledGraph, C::Array{Symbol, 1})
```

弦グラフ 'H' の消去順序を返します。'C' の頂点は最後に現れます。

弦グラフ `H` がグラフ `G` の消去順序 π から作成された場合、`C` が `H` のクリークであれば、返される `H` の消去順序は π の木幅と等しくなります。

このアルゴリズムは Shutski et al によって説明されています https://arxiv.org/abs/1911.12242
