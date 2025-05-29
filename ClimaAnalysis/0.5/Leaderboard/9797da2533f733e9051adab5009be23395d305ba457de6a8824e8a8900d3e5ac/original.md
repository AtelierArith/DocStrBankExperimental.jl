```
Base.setindex!(rmse_var::RMSEVariable, rmse, model_name::String)
```

Store a value or values from an array into the array of root mean squared errors in `rmse_var`. Support indexing by `String`. Do not support linear indexing.
