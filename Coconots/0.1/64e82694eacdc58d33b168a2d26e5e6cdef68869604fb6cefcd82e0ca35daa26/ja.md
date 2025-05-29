```
compute_scores(cocoReg_fit, max_x = 50)
```

フィッティングされたカウント回帰モデルのスコアリング指標を計算します。スコアには、対数スコア、二次スコア、および順位確率スコアが含まれます。

# 引数

  * `cocoReg_fit`: `"data"`、`"parameter"`、`"order"`、`"type"` などのキーを持つフィッティングされたモデルの結果を含む辞書で、オプションで `"covariates"` と `"max_loop"` も含まれます。
  * `max_x`（オプション）: 確率質量関数を合計する際に使用する最大カウント値（デフォルトは50）。

# 戻り値

以下のキーを持つ辞書:

  * `"logarithmic_score"`: 観測されたカウントの平均負の対数確率。
  * `"quadratic_score"`: 計算された確率とh-indexに基づく平均二次スコア。
  * `"ranked_probability_score"`: 平均順位確率スコア。
