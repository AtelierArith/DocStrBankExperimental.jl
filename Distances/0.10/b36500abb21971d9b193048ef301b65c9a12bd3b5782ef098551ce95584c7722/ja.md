```
pairwise!(metric::PreMetric, r::AbstractMatrix, a, b=a)
```

コレクション `a` の各要素とコレクション `b` の各要素との距離を距離 `metric` に従って計算し、その結果を `r` に格納します。単一のイテラブル `a` が提供された場合、その要素間の距離を計算します。

`r` はサイズ `length(a) × length(b)` の行列でなければなりません。
