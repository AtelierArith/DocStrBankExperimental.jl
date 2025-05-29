```
calculate_shared_production(::AbstractGroupNC, ECModel::AbstractEC; kwargs...)
```

非協力的なケースにおける共有生産エネルギーを計算します。非協力的なケースでは、ユーザー間に共有エネルギーはなく、自己生産のみです。出力は、per_unitがtrueのとき、需要に対して正規化されます。

''' 出力 –––- shared*en*frac : DenseAxisArray     各ユーザーの共有エネルギーと集約 '''
