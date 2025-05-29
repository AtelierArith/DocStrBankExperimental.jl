```
calculate_shared_production(::AbstractGroupANC, ECModel::AbstractEC; per_unit::Bool=true, only_shared::Bool=false)
```

集約非協力ケースのための共有生産エネルギーを計算します。この場合、ユーザー間で共有エネルギーが存在する可能性があり、自己生産だけではありません。only*sharedがfalseの場合、自己生産も考慮されますが、そうでない場合は共有エネルギーのみが考慮されます。共有エネルギーとは、各ユーザー間で共有されるエネルギーを意味します。出力は、per*unitがtrueのときに需要に対して正規化されます。

''' 出力 –––- shared*en*frac : DenseAxisArray     各ユーザーおよび集約のための共有エネルギー '''
