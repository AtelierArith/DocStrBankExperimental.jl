```
Monotonicer()
```

Monotonic filter to detect and normalize two types of dataset: 

  * daily monotonic
  * entirely non-decreasing/non-increasing data

Example: 

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

Implements: `fit!`, `transform!`
