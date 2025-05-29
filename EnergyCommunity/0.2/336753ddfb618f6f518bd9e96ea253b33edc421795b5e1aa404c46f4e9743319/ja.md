```
calculate_grid_import(::AbstractGroupANC, ECModel::AbstractEC; per_unit::Bool=true)
```

集約非協力ケースのためのグリッド使用量を計算します。出力は、per*unitがtrueのときに需要に対して正規化されています ''' 出力 –––- grid*frac : DenseAxisArray     各ユーザーのグリッド需要に対する依存度と集約 '''
