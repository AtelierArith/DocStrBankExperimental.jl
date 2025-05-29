```
calculate_self_production(ECModel::AbstractEC; per_unit::Bool=true, only_shared::Bool=false)
```

各ユーザーの自己生産を計算します。per_unitがtrueのとき、出力は需要に対して正規化されます。

''' 出力 –––- shared*ja*frac : DenseAxisArray     各ユーザーの共有エネルギーと集約 '''
