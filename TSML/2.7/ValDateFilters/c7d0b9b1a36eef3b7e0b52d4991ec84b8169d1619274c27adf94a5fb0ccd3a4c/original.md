```
CSVDateValWriter(
   Dict(
      :filename => "",
      :dateformat => ""
   )
)
```

Writes the time series dataframe into a file with the given date format.

Example:

```
inputfile =joinpath(dirname(pathof(TSML)),"../data/testdata.csv")
outputfile = joinpath("/tmp/test.csv")
csvreader = CSVDateValReader(Dict(:filename=>inputfile,:dateformat=>"d/m/y H:M"))
csvwtr = CSVDateValWriter(Dict(:filename=>outputfile,:dateformat=>"d/m/y H:M"))
filter1 = DateValgator()
filter2 = DateValNNer(Dict(:nnsize=>1))
mypipeline = @pipeline csvreader |> filter1 |> filter2 |> csvwtr
res=fit_transform!(mypipeline)

# read back what was written to validate
csvreader = CSVDateValReader(Dict(:filename=>outputfile,:dateformat=>"y-m-d HH:MM:SS"))
fit!(csvreader)
transform!(csvreader)
```

Implements: `fit!`, `transform!`
