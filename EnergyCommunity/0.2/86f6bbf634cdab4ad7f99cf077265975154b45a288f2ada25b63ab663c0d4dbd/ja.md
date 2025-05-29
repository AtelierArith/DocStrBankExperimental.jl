```
calculate_shared_consumption(::AbstractGroupNC, ECModel::AbstractEC; kwargs...)
```

各ユーザーが自分のソースまたは他のユーザーから満たす需要を計算します。非協力的なケースでは、共有エネルギーはなく、自己消費のみです。共有エネルギーとは、出力が真のときに需要に対して正規化されるエネルギーを意味します。

''' 出力 –––- shared*cons*frac : DenseAxisArray     各ユーザーの共有消費と集約 '''
