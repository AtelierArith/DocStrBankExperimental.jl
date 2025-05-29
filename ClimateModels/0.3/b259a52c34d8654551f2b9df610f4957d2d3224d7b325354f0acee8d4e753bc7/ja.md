```
pathof(x::AbstractModelConfig,subfolder::String)
```

`pathof(joinpath(x,subfolder))` または `joinpath(pathof(x),subfolder)` と同じです。
