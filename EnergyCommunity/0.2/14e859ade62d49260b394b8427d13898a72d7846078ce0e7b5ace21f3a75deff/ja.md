```
calculate_shared_consumption(ECModel::AbstractEC; per_unit::Bool=true)
```

各ユーザーが自分のソースまたは他のユーザーを使用して満たす需要を計算します。sharedがfalseの場合は自己消費も考慮されますが、そうでない場合は共有消費のみが考慮されます。出力は、per_unitがtrueの場合の需要に対して正規化されています。

''' 出力 –––- shared*cons*frac : DenseAxisArray     各ユーザーの共有消費と集計 '''
