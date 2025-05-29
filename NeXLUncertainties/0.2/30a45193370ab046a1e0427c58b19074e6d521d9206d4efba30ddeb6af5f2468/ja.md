```
ParallelMeasurementModel <: MeasurementModel
```

`ParallelMeasurementModel`は、同じ入力（または同じ入力のサブセット）を共有するため、同時に実行できる`MeasurementModel`のコレクションです。`ParallelMeasurementModel`は、スレッド化でき、ヤコビ行列の結合がより計算効率的であるため、`ComposedMeasurementModel`よりも優先されるべきです。

```
ParallelMeasurementModel(models::AbstractVector{MeasurementModel}, multithread=false)
```

`ParallelMeasurementModel`はマルチスレッドをサポートしていますが、マルチスレッドは計算のコストがスレッドを作成し管理するために必要なオーバーヘッドを超える場合にのみ使用すべきです。通常、これは、大規模な計算の外側のステップの1つで`multithread=true`を使用することを意味し、計算を分割することでヤコビ行列を可能な限り小さく保つことができます。

`ParallelMeasurementModel`の結果は、各モデルからの出力の和集合です。
