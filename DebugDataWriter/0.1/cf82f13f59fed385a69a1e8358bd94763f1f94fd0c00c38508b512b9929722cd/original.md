```
@debug_output debug_id title data_or_func
```

`debug_id` in fact is a name of output sub-directory

`title` is used as a name of the output file in that directory to distinguish output data. All non alpha-num symbols are translated into the `_` character.

`data_or_func`. The data for debug output might be provided as a literal, a variable or a lambda function. The lambda-function will be activated if only `enable_dump` is true.    
