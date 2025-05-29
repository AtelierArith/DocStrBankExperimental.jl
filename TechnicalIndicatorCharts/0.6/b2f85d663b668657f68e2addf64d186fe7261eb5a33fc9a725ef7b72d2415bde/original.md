```julia
visualize(
    unimplemented,
    opts,
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

This is a visualize method that's a catch-all for indicators that haven't had a visualize method made for them yet.  For now, it returns `missing`.
