```
skewness(x; method=:moment)
```

指定された方法を使用して歪度を計算します。

# 方法

  * モーメント（デフォルト）
  * フィッシャー-ピアソン
  * サンプル

# 引数

  * `x`:          値のベクトル。
  * `method`:     推定方法： `:moment`、 `:fisher_pearson` または `:sample`。
