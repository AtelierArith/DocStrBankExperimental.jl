```
MeasurementData(measurement_probability::MeasurementProbability{T}, NM::Int) where T <: Union{Nothing, AbstractMeasurementSetting}
```

指定された測定確率に基づいて、`NM` 個の射影測定をサンプリングすることによって `MeasurementData` オブジェクトを返します。

# 引数

  * `measurement_probability::MeasurementProbability`: 測定確率（ITensor）と関連設定を含むコンテナ。
  * `NM::Int`: サンプリングする射影測定の数。

# 返り値

測定確率から推測される次元を持つ `MeasurementData` オブジェクト。
