```
offset_representatives!(g::PeriodicGraph, offsets)
```

グラフ `g` をインプレースで修正し、新しい初期セルの `i` 番目の頂点が前の初期セルに対する `offsets[i]` のセルの `i` 番目の頂点に対応するようにします。

!!! note
    結果として得られるグラフは初期のものと同型ですが、表現が変更されています。

