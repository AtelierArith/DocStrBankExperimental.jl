```
calculate_grid_export(ECModel::AbstractEC; per_unit::Bool=true)
```

エネルギーコミュニティとユーザーのためのグリッドエクスポートを計算します。per_unitがtrueのとき、出力は需要に対して正規化されます。

''' 出力 –––- grid_frac : DenseAxisArray     各ユーザーのグリッド需要に対する依存度と集約 '''
