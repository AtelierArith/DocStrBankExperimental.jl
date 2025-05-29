```
Outliernicer(Dict(
   :dateinterval => Dates.Hour(1),
   :nnsize => 1,
   :missdirection => :symmetric,
   :scale => 1.25
))
```

中央値-スケール*iqrまたは中央値+スケール*iqrの下または上の外れ値を検出し、DateValNNerを呼び出して最近傍で置き換えます。

例:

```
fname = joinpath(dirname(pathof(TSML)),"../data/testdata.csv")
csvfilter = CSVDateValReader(Dict(:filename=>fname,:dateformat=>"dd/mm/yyyy HH:MM"))
valgator = DateValgator(Dict(:dateinterval=>Dates.Hour(1)))
valnner = DateValNNer(Dict(:dateinterval=>Dates.Hour(1)))
stfier = Statifier(Dict(:processmissing=>true))
mono = Monotonicer(Dict())
outliernicer = Outliernicer(Dict(:dateinterval=>Dates.Hour(1)))

mpipeline = @pipeline csvfilter |> valgator |> mono |> valnner |> outliernicer |> stfier
results = fit_transform!(mpipeline)
```

実装: `fit!`, `transform!`
