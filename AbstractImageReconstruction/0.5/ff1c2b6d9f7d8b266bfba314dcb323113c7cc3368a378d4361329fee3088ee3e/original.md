```
toDictValue!(dict, value)
```

Extracts the value-representation of `value` and adds it to `dict`. The default implementation for structs with fields adds each field of the argument as a key-value pair with the value being provided by the `toDictValue` function.
