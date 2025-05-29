```
OneTimescaleAndOscWithMissing
```

オシレーションと欠損データの両方を扱う時系列分析のためのモジュール。NaN値を処理するための専門的なメソッドを使用します：

  * ACFの場合：ギャップを適切に処理するためにcomp*ac*time_missingを使用
  * PSDの場合：不規則なサンプリングのためにLomb-Scargle周期グラムを使用
