```
checkpoint_fullname(x::IndexEntry)
```

The full name of the checkpoint output file, including [`prefixes`](@ref), and [`checkpoint_name`](@ref). If the checkpoint was saved using `checkpoint(Forecasters, "forecasts", ...)` then `checkpoint_fullname` will return `"Forecasters.forecasts"`. If the checkpoint was saved using `checkpoint("Foo.Bar", "forecasts.jlso")` then `checkpoint_fullname` will return `"Foo.Bar.forecasts"`.
