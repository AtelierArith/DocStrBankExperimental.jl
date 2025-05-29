```
resolve(datadep, inner_filepath, calling_filepath)
```

Returns a path to the folder containing the datadep. Even if that means downloading the dependency and putting it in there.

```
 - `inner_filepath` is the path to the file within the data dir
 - `calling_filepath` is a path to the file where this is being invoked from
```

This is basically the function the lives behind the string macro `datadep"DepName/inner_filepath"`.
