```
Data(table)
Data(; url, [format], [name])
Data(generator::SymbolOrString; properties...)
```

Creates a `DataSpec` containing the `data` property of a viewable specification. Available constructors are:

  * using a `table` that supports the [Tables.jl interface](https://github.com/JuliaData/Tables.jl)
  * using a `url` to load the data from, with optional `format` and `name` properties. [](https://vega.github.io/vega-lite/docs/data.html#url)
  * using a `generator` with specific `properties` to a use any of the available [Vega-Lite data generator](https://vega.github.io/vega-lite/docs/data.html#data-generators)

See more in [Vega-Lite's](https://vega.github.io/vega-lite/docs/data.html) and [Deneb's](https://brucala.github.io/Deneb.jl/dev/data_mark_encoding/#Data) documentation.

# Examples

```
# table format
data = (a=[1, 2], b=["potato", "tomato"])
Data(data)

# data from url
Data(
    url="https://vega.github.io/vega-datasets/data/us-10m.json",
    format=(type=:topojson, feature=:states),
)

# Vega-Lite gererator
Data(:graticule, step=[15, 15])
```
