```
build_df_data(vDF::Vector{DataFrame}) => DataFrame
```

It checks all samples and includes all the variables names. If a sample misses one or more variable, it generates the missing entries for all variables. It returns a dataframe.   
