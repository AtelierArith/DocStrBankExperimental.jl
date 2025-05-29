```
function predict_out_of_sample(rr::ridgeRegRes, df::AbstractDataFrame; dropmissingvalues=true)

Similar to `predict_in_sample` although it does not expect a response variable nor produce statistics requiring a response variable.
```
