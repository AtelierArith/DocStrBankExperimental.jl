```
get_diffs(mg::MetaGraphsNext.MetaGraph)
```

mg.graph_data[:models]に保存されたJuMPモデルを使用して、各リーフ/変電所接続での電力注入/負荷の差と|v|を計算します。

三つの`Float64[]`を返します。
