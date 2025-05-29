```
deaadd(X, Y, model)
```

入力 `X` と出力 `Y` の関連データ包絡分析加重加法モデルを計算します。

モデル仕様：

  * `:Ones`: 標準加法DEAモデル。
  * `:MIP`: 非効率性比率の測定。(Charnes et al., 1987; Cooper et al., 1999)
  * `:Normalized`: 正規化加重加法DEAモデル。(Lovell and Pastor, 1995)
  * `:RAM`: 範囲調整測定。(Cooper et al., 1999)
  * `:BAM`: 制約調整測定。(Cooper et al, 2011)
  * `:Custom`: ユーザー提供の重み。

# オプション引数

  * `orient=:Graph`: グラフ指向 `:Graph`、入力指向 `:Input`、または出力指向モデル `:Output` のいずれかを選択します。
  * `rts=:VRS`: 定常規模の収益 `:CRS` または変動規模の収益 `:VRS` のいずれかを選択します。
  * `rhoX`: 入力の重みの行列。`model=:Custom` の場合のみ。
  * `rhoY`: 出力の重みの行列。`model=:Custom` の場合のみ。
  * `Xref=X`: ユニットが評価される基準となる入力の参照セットを特定します。
  * `Yref=Y`: ユニットが評価される基準となる出力の参照セットを特定します。
  * `disposX=:Strong`: 入力の強い可処分性を選択します。弱い可処分性を選択するには `:Weak` を選択します。
  * `disposY=:Strong`: 出力の強い可処分性を選択します。弱い可処分性を選択するには `:Weak` を選択します。
  * `names`: 意思決定単位の名前を含む文字列のベクター。
