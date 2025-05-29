```
function predict_in_sample(lr::linRegRes, df::AbstractDataFrame; α=0.05, req_stats=["none"], dropmissingvalues=true)

Using the estimated coefficients from the regression make predictions, and calculate related statistics.
```
