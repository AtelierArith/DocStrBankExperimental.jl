```
deaaddweights(X, Y, model)
```

入力 `X` と出力 `Y` に対する関連データ包絡分析加重加法モデルの対応する重みを計算します。

モデル仕様:

  * `:Ones`: 標準加法DEAモデル。
  * `:MIP`: 非効率性比率の測定。(Charnes et al., 1987; Cooper et al., 1999)
  * `:Normalized`: 正規化加重加法DEAモデル。(Lovell and Pastor, 1995)
  * `:RAM`: 範囲調整測定。(Cooper et al., 1999)
  * `:BAM`: 制約付き調整測定。(Cooper et al, 2011)

# オプション引数

  * `orient=:Graph`: グラフ指向 `:Graph`、入力指向 `:Input`、または出力指向モデル `:Output` のいずれかを選択します。
