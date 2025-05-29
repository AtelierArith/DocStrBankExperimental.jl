```
DateValgator(args=Dict())
   Dict(
    :dateinterval => Dates.Hour(1),
    :aggregator => :median
  )
)
```

指定された日付期間に基づいて値を集約します。

例:

```
# 欠損データを含むランダムな値を生成
Random.seed!(123)
gdate = DateTime(2014,1,1):Dates.Minute(15):DateTime(2016,1,1)
gval = Array{Union{Missing,Float64}}(rand(length(gdate)))
gmissing = 50000
gndxmissing = Random.shuffle(1:length(gdate))[1:gmissing]
X = DataFrame(Date=gdate,Value=gval)
X.Value[gndxmissing] .= missing

dtvlmean = DateValgator(Dict(
      :dateinterval=>Dates.Hour(1),
      :aggregator => :mean))
fit!(dtvlmean,X)
res = transform!(dtvlmean,X)
```

実装: `fit!`, `transform!`
