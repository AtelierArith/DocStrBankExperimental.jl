```
cpufeatures() ::Vector{Symbol}
```

Get a list of symbols of all cpu supported features.  Might be extensive and not exactly useful other than for testing purposes.  Also, this implementation is not efficient since each feature is queried independently.
