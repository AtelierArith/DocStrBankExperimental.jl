```
CSVDateValWriter(
   Dict(
      :filename => "",
      :dateformat => ""
   )
)
```

指定された日付形式で時系列データフレームをファイルに書き込みます。

例:

```
inputfile =joinpath(dirname(pathof(TSML)),"../data/testdata.csv")
outputfile = joinpath("/tmp/test.csv")
csvreader = CSVDateValReader(Dict(:filename=>inputfile,:dateformat=>"d/m/y H:M"))
csvwtr = CSVDateValWriter(Dict(:filename=>outputfile,:dateformat=>"d/m/y H:M"))
filter1 = DateValgator()
filter2 = DateValNNer(Dict(:nnsize=>1))
mypipeline = @pipeline csvreader |> filter1 |> filter2 |> csvwtr
res=fit_transform!(mypipeline)

# 検証のために書き込まれた内容を読み戻す
csvreader = CSVDateValReader(Dict(:filename=>outputfile,:dateformat=>"y-m-d HH:MM:SS"))
fit!(csvreader)
transform!(csvreader)
```

実装: `fit!`, `transform!`
