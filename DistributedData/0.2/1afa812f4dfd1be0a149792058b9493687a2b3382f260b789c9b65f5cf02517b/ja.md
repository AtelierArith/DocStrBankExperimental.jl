```
dapply_cols(dInfo::Dinfo, fn, columns::Vector{Int})
```

分散データセットの列に関数 `fn` を適用します。

`fn` は *2* つのパラメータを受け取ります：

  * データベクトル（1 つのワーカーに保存された全列）
  * `columns` 配列内の列のインデックス（すなわち `1:length(columns)` の数）
