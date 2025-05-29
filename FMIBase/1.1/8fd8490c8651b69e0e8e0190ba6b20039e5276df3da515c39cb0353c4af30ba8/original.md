```
statusToString(::struct, status::Union{fmi2Status, Integer})
```

Converts `fmi2Status` `status` into a String ("OK", "Warning", "Discard", "Error", "Fatal", "Pending").
