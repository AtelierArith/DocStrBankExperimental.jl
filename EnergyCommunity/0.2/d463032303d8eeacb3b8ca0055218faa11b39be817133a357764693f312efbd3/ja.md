```
calculate_grid_export(::AbstractGroupNC, ECModel::AbstractEC; per_unit::Bool=true)
```

非協力的なケースのためのグリッド輸出を計算します。per_unitがtrueのとき、出力は需要に対して正規化されます。

''' 出力 –––- grid_frac : DenseAxisArray     各ユーザーのグリッド需要への依存度と集約 '''
