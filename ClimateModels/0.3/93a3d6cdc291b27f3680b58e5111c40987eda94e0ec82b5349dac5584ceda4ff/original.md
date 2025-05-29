```
pathof(x::AbstractModelConfig)
```

Returns the run directory path for x ; i.e. `joinpath(x.folder,string(x.ID))`
