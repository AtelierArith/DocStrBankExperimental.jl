```
MovingTimeWindow{T<:TimeType, S}(window::Dates.Period)
MovingTimeWindow(window::Dates.Period; valtype=Float64, timetype=Date)
```

タイムスタンプに基づいてデータの移動ウィンドウをフィットします。各観測値は、最初のアイテムが `<: Dates.TimeType` である `Tuple`、`NamedTuple`、または `Pair` でなければなりません。`timestamp` が次の範囲にない観測値は、

```
now() - window ≤ timestamp ≤ now()
```

すべての `fit!` の実行時に破棄されます。

# 例

```
using Dates
dts = Date(2010):Day(1):Date(2011)
y = rand(length(dts))

o = MovingTimeWindow(Day(4); timetype=Date, valtype=Float64)
fit!(o, zip(dts, y))
```
