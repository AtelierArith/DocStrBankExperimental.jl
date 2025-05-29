```
Base.getindex(rmse_var::RMSEVariable, model_name, category)
```

Return a subset of the array holding the root mean square errors as specified by `model_name` and `category`. Support indexing by `String` and `Int`.
