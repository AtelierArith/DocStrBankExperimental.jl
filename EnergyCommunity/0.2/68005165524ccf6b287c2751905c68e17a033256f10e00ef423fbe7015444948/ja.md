```
calculate_production_shares(ECModel::AbstractEC; per_unit::Bool=true)
```

エネルギー生産資源によるエネルギー比率を一般的なグループのために計算します。per_unitがtrueのとき、出力は需要に対して正規化されます。'''

# 出力

frac : DenseAxisArray     ユーザーおよび全システムによるエネルギー資源別のエネルギー生産のシェアを説明するDenseAxisArrayで、対応するグループの需要に対して正規化されています。

'''
