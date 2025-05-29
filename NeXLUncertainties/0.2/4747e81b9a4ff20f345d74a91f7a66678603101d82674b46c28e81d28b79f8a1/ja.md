```
ComposedMeasurementModel <: MeasurementModel
```

`ComposedMeasurementModel`は、ステップiの出力が次のステップで使用される場合に使用されます。同じ入力（または同じ入力のサブセット）を共有する`MeasurementModel`のコレクションがある場合は、`ParallelMeasurementModel`を優先してください。`ParallelMeasurementModel`は複数のスレッドで実行でき、ヤコビアンを掛け算するのではなく連結することができます。`ParallelMeasurementModel`と`ComposedMeasurementModel`を組み合わせることで、効率的な計算モデルを生成できます。

`ComposedMeasurementModel`の最終結果は、最終ステップの出力です。
