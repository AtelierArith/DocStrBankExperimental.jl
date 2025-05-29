```
deaprofitadd(X, Y, W, P, model)
```

データ包絡分析加重加算モデルを使用して、入力 `X`、出力 `Y`、入力の価格 `W`、および出力の価格 `P` に基づいて利益効率を計算します。

モデル仕様：

  * `:Ones`: 標準加算DEAモデル。
  * `:MIP`: 非効率性比率の測定。(Charnes et al., 1987; Cooper et al., 1999)
  * `:Normalized`: 正規化加重加算DEAモデル。(Lovell and Pastor, 1995)
  * `:RAM`: 範囲調整測定。(Cooper et al., 1999)
  * `:BAM`: 制約付き調整測定。(Cooper et al, 2011)
  * `:Custom`: ユーザー提供の重み。

# オプション引数

  * `rhoX`: 入力の重みの行列。`model=:Custom` の場合のみ。
  * `rhoY`: 出力の重みの行列。`model=:Custom` の場合のみ。
  * `monetary=false`: 正規化された用語での分解。`true` の場合は貨幣用語。
  * `names`: 意思決定単位の名前を含む文字列のベクトル。
