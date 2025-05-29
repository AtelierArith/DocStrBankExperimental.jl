```
OneTimescaleWithMissing
```

欠損データを含む時系列分析を扱うためのモジュール。NaN値を処理するための専門的なメソッドを使用します：

  * ACFの場合：comp*ac*time_missingを使用（missing="conservative"のstatsmodels.tsa.statstools.acfに相当）
  * PSDの場合：不規則なサンプリングを処理するためにLomb-Scargle周期グラムを使用します
