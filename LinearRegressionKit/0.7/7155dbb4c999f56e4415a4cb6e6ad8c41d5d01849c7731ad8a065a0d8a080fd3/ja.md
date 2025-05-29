```
function predict_in_sample(lr::linRegRes, df::AbstractDataFrame; α=0.05, req_stats=["none"], dropmissingvalues=true)

回帰から推定された係数を使用して予測を行い、関連する統計を計算します。
```
