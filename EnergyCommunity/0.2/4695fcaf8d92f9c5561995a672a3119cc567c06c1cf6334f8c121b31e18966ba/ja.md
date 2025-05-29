```
calculate_shared_consumption(::AbstractGroupANC, ECModel::AbstractEC; per_unit::Bool=true, only_shared::Bool=false)
```

各ユーザーが自分のソースまたは他のユーザーから満たす需要を、集約非協力ケースのために計算します。この場合、共有エネルギーがあり、自己消費だけではありません。only*sharedがfalseの場合、自己消費も考慮されますが、そうでない場合は共有エネルギーのみが考慮されます。共有エネルギーとは、各ユーザー間で共有されるエネルギーを意味します。出力は、per*unitがtrueの場合、需要に対して正規化されます。

''' 出力 –––- shared*cons*frac : DenseAxisArray     各ユーザーの共有消費と集約 '''
