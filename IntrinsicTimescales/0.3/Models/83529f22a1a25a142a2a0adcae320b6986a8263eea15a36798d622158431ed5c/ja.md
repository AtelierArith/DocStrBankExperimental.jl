```
check_model_inputs(data, time, fit_method, summary_method, prior, acwtypes, distance_method)
```

タイムスケールモデル構築のための入力を検証します。

# 引数

  * `data`: 入力時系列データ
  * `time`: データに対応する時間点
  * `fit_method`: フィッティング方法 (:abc, :advi)
  * `summary_method`: サマリー統計の種類 (:psd または :acf)
  * `prior`: パラメータの事前分布
  * `acwtypes`: ACW分析の種類
  * `distance_method`: 距離メトリックの種類 (:linear または :logarithmic)

# 例外

  * `ArgumentError`: いずれかの入力が無効または互換性がない場合
