```
calculate_grid_import(::AbstractGroupNC, ECModel::AbstractEC; per_unit::Bool=true)
```

非協力的なケースのためのグリッド使用量を計算します。出力は、per_unitがtrueの場合、需要に対して正規化されます。

''' 出力 –––- grid_frac : DenseAxisArray     各ユーザーのグリッド需要に対する依存度と集約 '''
