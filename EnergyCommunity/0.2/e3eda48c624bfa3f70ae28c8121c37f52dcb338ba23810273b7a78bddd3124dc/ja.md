```
calculate_shared_production(::AbstractGroupCO, ECModel::AbstractEC; per_unit::Bool=true, only_shared::Bool=false)
```

協同ケースのために共有されたエネルギーを計算します。協同ケースでは、ユーザー間で共有されるエネルギーがあり、自己生産だけではありません。only*sharedがfalseの場合、自己生産も考慮されますが、そうでない場合は共有エネルギーのみが考慮されます。共有エネルギーとは、出力が需要に対して正規化されるエネルギーを意味します。per*unitがtrueの場合。

''' 出力 –––- shared*en*frac : DenseAxisArray     各ユーザーの共有エネルギーと集約 '''
