```
dataproperty(io, label)
```

Get a data property (data properties are per file, rather than per trace) from `io::JSeis` with label `label::String`.  For example, `dataproperty(jsopen("data.js"), "FREQUENCY")`.
