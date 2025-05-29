```
pathof(x::AbstractModelConfig,subfolder::String)
```

Same as `pathof(joinpath(x,subfolder))` or `joinpath(pathof(x),subfolder)`
