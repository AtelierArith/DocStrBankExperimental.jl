```
MeterProvider(;resource = Resource(), views = View[], max_metrics = nothing)
```

`views` が空の場合、すべてのメトリクスを有効にするためにデフォルトのもの（[`View(;instrument_name="*")`](@ref)）が追加されます。
