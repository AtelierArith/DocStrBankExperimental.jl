```
loadmodel!(estimator, filename)
```

フィッティングされたモデル `filename` を `estimator` にロードします。これは、`filename` として保存されたモデルのパラメータやデータではなく、フィッティングされたモデルのみをロードすることに注意してください。

# 引数

  * `estimator::LGBMEstimator`: 予測に使用する推定器。
  * `filename::String`: モデルが含まれているファイルの名前。
