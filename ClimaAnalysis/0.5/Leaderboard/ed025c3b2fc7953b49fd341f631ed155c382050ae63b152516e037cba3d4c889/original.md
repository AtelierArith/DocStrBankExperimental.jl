```
Base.getindex(rmse_var::RMSEVariable, model_name::String)
```

Return a subset of the array holding the root mean square errors as specified by `model_name`. Support indexing by `String`. Do not support linear indexing.
