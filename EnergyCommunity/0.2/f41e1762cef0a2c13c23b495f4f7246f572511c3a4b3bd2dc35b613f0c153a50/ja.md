```
calculate_grid_export(::AbstractGroupANC, ECModel::AbstractEC; per_unit::Bool=true)
```

集約非協力ケースのためのグリッド輸出を計算します。出力は、per*unitがtrueのときに需要に対して正規化されています ''' 出力 –––- grid*frac : DenseAxisArray     各ユーザーのグリッド需要への依存度と集約 '''
