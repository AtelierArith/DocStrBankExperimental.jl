```
Encoding(x; channels...)
Encoding(x, y; channels...)
Encoding(; channels...)
```

Creates an `EncodingSpec` containing the `encoding` property of a single or layer view specification. The `x` and `y` channels can be specified as positional arguments using the shorthad string syntax. See more in [Vega-Lite's](https://vega.github.io/vega-lite/docs/encoding.html) and [Deneb.jl's](https://brucala.github.io/Deneb.jl/dev/data_mark_encoding/#Encoding).

# Examples

```
Encoding("monthdate(date):T", "mean(precipitation):Q", color="year(date):O")
Encoding(
    x=field("bin_min:Q", bin=:binned, title="Maximum Daily Temperature (C)"),
    y=field("value:Q", scale=(range=[20, -20]), axis=nothing),
    fill=field="mean_temp:Q",
)
```
