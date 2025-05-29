```
TemperatureRamp <: Method
```

システムを解決するために、前の解を低い温度での初期推測として使用し、温度を下げるシステムを反復的に解決します。これにより、収束の問題に対処できる場合があります。

引数

  * `method`: 個々の温度に対してシステムを解決する方法。
  * `temperatures`: 考慮すべき温度。増加する値のベクトルでなければなりません。
  * `verbose`: 情報を印刷するかどうか。

例: `TemperatureRamp(NgIteration(), [0.1, 0.3, 0.4]; verbose=false)`
