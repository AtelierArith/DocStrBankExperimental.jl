```
vlspec(s)
```

特定のVega-Lite制約を強制するVega-Lite仕様を作成します。

# 例

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
