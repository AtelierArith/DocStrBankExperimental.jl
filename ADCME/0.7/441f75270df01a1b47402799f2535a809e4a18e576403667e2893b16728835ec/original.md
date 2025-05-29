```
get_library(filename::AbstractString)
```

Returns a valid library file. For example, for `filename = "adcme"`, we have 

  * On MacOS, the function returns `libadcme.dylib`
  * On Linux, the function returns `libadcme.so`
  * On Windows, the function returns `adcme.dll`
