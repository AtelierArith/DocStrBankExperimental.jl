```
vlspec(s)
```

Creates a Vega-Lite spec enforcing certain Vega-Lite constrains.

# Example

```julia
vlspec(
    data=(; url="https://vega.github.io/vega-datasets/data/seattle-weather.csv"),
    mark=:bar,
    encoding=(
        x=(timeUnit=:month, field=:date, type=:ordinal),
        y=(aggregate=:mean, field=:precipitation),
    )
)
```
