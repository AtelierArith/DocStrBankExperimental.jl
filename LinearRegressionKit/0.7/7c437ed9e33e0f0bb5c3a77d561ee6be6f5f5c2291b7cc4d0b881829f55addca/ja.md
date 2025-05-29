```
function predict_out_of_sample(rr::ridgeRegRes, df::AbstractDataFrame; dropmissingvalues=true)

`predict_in_sample`と似ていますが、応答変数を期待せず、応答変数を必要とする統計を生成しません。
```
