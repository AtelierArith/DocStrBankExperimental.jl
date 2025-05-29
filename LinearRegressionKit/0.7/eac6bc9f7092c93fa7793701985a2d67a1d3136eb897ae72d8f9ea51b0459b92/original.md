```
function predict_out_of_sample(lr::linRegRes, df::AbstractDataFrame; α=0.05, req_stats=["none"], dropmissingvalues=true)

Similar to `predict_in_sample` although it does not expect a response variable nor produce statistics requiring a response variable.
```
