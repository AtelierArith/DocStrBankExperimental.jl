```
savemodel(estimator, filename; [num_iteration = -1])
```

`estimator` にフィットしたモデルを `filename` として保存します。

# 引数

  * `estimator::LGBMEstimator`: 予測に使用するエスティメーター。
  * `filename::String`: モデルを保存するファイルの名前。
  * `num_iteration::Integer`: 保存するモデルのイテレーション数を設定するキーワード引数。 `< 0` はすべてのイテレーションを意味します。
  * `start_iteration` : 保存するべきイテレーションの開始インデックス。
  * `feature_importance_type` : 特徴の重要性のタイプで、C*API*FEATURE*IMPORTANCE*SPLIT または C*API*FEATURE*IMPORTANCE*GAIN のいずれかです。
