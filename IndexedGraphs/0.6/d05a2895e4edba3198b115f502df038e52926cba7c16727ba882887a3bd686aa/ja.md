```
bidirected_with_mappings(g::IndexedGraph) -> (gdir, dir2undir, undir2dir)
```

`IndexedGraph` `g` から `IndexedBiDiGraph` `gdir` を構築し、`g` の各無向辺に対して2つの有向辺を作成します。さらに、`g` の無向辺から `gdir` の対応する有向辺へのマッピングを含む2つのベクトルを返します。

### 出力

  * `gdir` – 有向グラフ
  * `dir2undir` – `gdir` の有向辺のインデックスを `g` の対応する無向辺にマッピングする整数のベクトル
  * `undir2dir` – 2つの整数を持つベクトルのベクトルで、`g` の無向辺のインデックスを `gdir` の2つの対応する有向辺にマッピングします

```
