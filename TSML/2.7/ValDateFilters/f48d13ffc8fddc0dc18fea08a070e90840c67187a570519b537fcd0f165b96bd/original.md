```
DateValgator(args=Dict())
   Dict(
    :dateinterval => Dates.Hour(1),
    :aggregator => :median
  )
)
```

Aggregates values based on date period specified.

Example:

```
# generate random values with missing data
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

Implements: `fit!`, `transform!`
