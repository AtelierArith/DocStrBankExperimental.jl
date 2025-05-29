```
Outliernicer(Dict(
   :dateinterval => Dates.Hour(1),
   :nnsize => 1,
   :missdirection => :symmetric,
   :scale => 1.25
))
```

Detects outliers below or above (median-scale*iqr,median+scale*iqr) and calls DateValNNer to replace them with nearest neighbors.

Example:

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

Implements: `fit!`, `transform!`
