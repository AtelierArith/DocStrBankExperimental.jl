```
calculate_self_consumption(ECModel::AbstractEC; per_unit::Bool=true)
```

各ユーザーが自分のソースを使用して満たす需要、または自己消費を計算します。出力は、per_unitがtrueの場合の需要に対して正規化されています。

''' 出力 –––- shared*cons*frac : DenseAxisArray     各ユーザーの共有消費と集計 '''
