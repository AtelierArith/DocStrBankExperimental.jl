```
deacostadditive(X, Y, W, model)
```

入力 `X`、出力 `Y`、および入力の価格 `W` に対して加法的データ包絡分析を使用してコスト効率を計算します。

モデル仕様：

  * `:Ones`: 標準的な加法DEAモデル。
  * `:MIP`: 非効率性比率の測定。(Charnes et al., 1987; Cooper et al., 1999)
  * `:Normalized`: 正規化された加重加法DEAモデル。(Lovell and Pastor, 1995)
  * `:RAM`: 範囲調整測定。(Cooper et al., 1999)
  * `:BAM`: 制約付き調整測定。(Cooper et al, 2011)
  * `:Custom`: ユーザー提供の重み。

# オプション引数

  * `rts=:VRS`: 変動規模の収益を選択します。定常的な収益を選択するには `:CRS` を選択します。
  * `rhoX`: 入力の重みの行列。`model=:Custom` の場合のみ。
  * `disposal=:Strong`: 出力の強い廃棄を選択します。弱い廃棄を選択するには `:Weak` を選択します。
  * `monetary=false`: 正規化された用語での分解。`true` の場合は貨幣用語。
  * `names`: 意思決定単位の名前を含む文字列のベクトル。
