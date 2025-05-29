```
prefixes(x::IndexEntry)
```

The prefixes of the checkpoint output file. This is a tuple of any prefixes specified. If the checkpoint was saved used `checkpoint(Forecasters, "forecasts", ...)` then it's `prefixes` are `("Forecasters",)`. Generally in practice there are either one matching the module the checkpoint was declared in (as in the previous example), or zero if it wasn't specified (as in `checkpoint("forecasts",...)`). If it was saved as `checkpoint("Foo.Bar", "forecasts.jlso")` then prefixed will return `("Foo", "Bar")`.
