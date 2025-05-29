```
mt_ccvf(S; <キーワード引数>)
```

単変量マルチテーパー交差共分散/交差相関関数を計算します。MTSpectrum構造体を入力します。

...

# 引数

  * `S::MTSpectrum`: `multispec`への多変量呼び出しの結果を含むベクトル
  * `typ::Symbol = :ccvf`: 交差相関関数(:ccf)または交差共分散関数(:ccvf)を計算するかどうか

...

...

# 出力

  * `MtCrossCovarianceFunction`、`MTCrossCorrelationFunction`は、上記の`typ`入力の選択に応じて異なります。

...

参照: [`multispec`](@ref) ```
