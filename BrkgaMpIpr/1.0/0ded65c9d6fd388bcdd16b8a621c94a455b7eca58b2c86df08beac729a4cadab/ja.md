```
@enum PathRelinkingResult
```

パスリリンク手続きの結果タイプ/ステータスを指定します：

  * `TOO_HOMOGENEOUS`: 集団間の染色体があまりにも均質であり、パスリリンクは改善された解を生成しません。
  * `NO_IMPROVEMENT`: パスリリンクは行われましたが、改善された解は見つかりませんでした。
  * `ELITE_IMPROVEMENT`: エリートセットの中で改善された解が見つかりましたが、最良の解は改善されませんでした。
  * `BEST_IMPROVEMENT`: 最良の解が改善されました。
