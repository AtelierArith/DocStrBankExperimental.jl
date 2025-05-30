```julia
visualize(
    unimplemented,
    opts,
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

これは、まだ視覚化メソッドが作成されていないインジケーターのためのキャッチオールの visualize メソッドです。 現在のところ、`missing` を返します。
