```
Statifier(Dict(
   :processmissing => true
))
```

出力は、平均、中央値、四分位数、エントロピー、尖度、歪度などの要約統計量で、パラメータは次のとおりです：

  * `:processmissing` => `boolean` は、`missing` データの統計を含めるかどうかを示します。

例：

```
dt=[missing;rand(1:10,3);missing;missing;missing;rand(1:5,3)]
dat = DataFrame(Date= DateTime(2017,12,31,1):Dates.Hour(1):DateTime(2017,12,31,10) |> collect,
                Value = dt)

statfier = Statifier(Dict(:processmissing=>false))

fit!(statfier,dat)
results=transform!(statfier,dat)
```

実装： `fit!`, `transform!`
