```
calculate_shared_production(ECModel::AbstractEC; per_unit::Bool=true)
```

各ユーザーが自分のPODで生産し使用するエネルギー、またはEC内で商業的に消費されるエネルギーを計算します。sharedがfalseの場合は自己生産も考慮されますが、そうでない場合は共有エネルギーのみが考慮されます。出力は、per_unitがtrueの場合、需要に対して正規化されます。

''' 出力 –––- shared*cons*frac : DenseAxisArray     各ユーザーの共有消費と集計 '''
