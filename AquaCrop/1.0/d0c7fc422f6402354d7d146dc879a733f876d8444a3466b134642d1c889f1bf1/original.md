```
cropfield, all_ok = start_cropfield(; kwargs...)
```

Starts the `cropfield::AquaCropField` with the proper runtype. it uses default values for `runtype` and `parentdir` if these `kwargs` are missing.

It returns a `cropfield` with default values for crop, soil, etc. After calling this function check if `all_ok.logi == true`
