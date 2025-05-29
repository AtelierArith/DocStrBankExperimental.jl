```
calculate_grid_export(::AbstractGroupCO, ECModel::AbstractEC; per_unit::Bool=true)
```

協同ケースのためのグリッドエクスポートを計算します。出力は、per*unitがtrueのときに需要に対して正規化されます ''' 出力 –––- grid*frac : DenseAxisArray     各ユーザーのグリッド需要への依存と集約 '''
