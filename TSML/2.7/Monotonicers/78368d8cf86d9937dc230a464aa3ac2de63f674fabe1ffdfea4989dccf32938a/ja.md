```
Monotonicer()
```

モノトニックフィルターは、2種類のデータセットを検出して正規化します：

  * 日次モノトニック
  * 完全に非減少/非増加のデータ

例：

```
fname = joinpath(dirname(pathof(TSML)),"../data/testdata.csv")
csvfilter = CSVDateValReader(Dict(:filename=>fname,:dateformat=>"dd/mm/yyyy HH:MM"))
valgator = DateValgator(Dict(:dateinterval=>Dates.Hour(1)))
valnner = DateValNNer(Dict(:dateinterval=>Dates.Hour(1)))
stfier = Statifier(Dict(:processmissing=>true))
mono = Monotonicer(Dict())

mypipeline = @pipeline csvfilter |> valgator |> mono |> stfier
result = fit_transform!(mypipeline)
```

実装： `fit!`, `transform!`
